#!/usr/bin/env groovy
@Library('jenkins-custom-library')_
pipeline{
	agent any
	environment {
		TEMP_DIR = '/dev/shm/raspios'

		ZULIP_PROPS = readProperties file: "${WORKSPACE}/properties/zulip_prop"
		MAIN_STREAM = "${ZULIP_PROPS['MAIN_STREAM']}"
	}
	stages {
		stage("Checkout GIT") {
			steps {
				withCredentials([usernamePassword(credentialsId: '5b25baba-433c-41a9-b104-59e49ec74e49', passwordVariable: 'JENKINS_TOKEN', usernameVariable: 'JENKINS_USERNAME')]){
					script {
						def vars = checkout(scm: [$class: 'GitSCM',
							branches: [[name: 'main']],
							userRemoteConfigs: [[url: 'https://github.com/mechatrax/pi-protect']]
						], poll: true)
						def msg = sh(
							script: 'git log --decorate=no --oneline | sed -e \'s/[0-9a-f]\\+ //\' | grep ^Release | head -1',
							returnStdout: true
						).trim()
						if ( ! msg.contains("Release") ) {
							sh 'curl -s -X POST -u ${JENKINS_USERNAME}:${JENKINS_TOKEN} http://127.0.0.1:8080/job/${JOB_NAME}/${BUILD_NUMBER}/stop'
						}
						env.RELEASE_NAME = msg.replaceFirst('Release.*(piprotect[^ ]+).*', '$1')
						if ( env.RELEASE_NAME == "" ) {
							sh 'curl -s -X POST -u ${JENKINS_USERNAME}:${JENKINS_TOKEN} http://127.0.0.1:8080/job/${JOB_NAME}/${BUILD_NUMBER}/stop'
						}
						env.SUM_FILE = 'piprotect_lite_arm64.sha256sum'
					}
				}
			}
		}
		stage("Upload") {
			steps {
				withCredentials([
				usernamePassword(credentialsId: 'aa4ddfcc-11d9-418d-b794-8963612b6a78', passwordVariable: 'FTP_PASSWORD', usernameVariable: 'FTP_USERNAME'),
				string(credentialsId: '0e3efab3-616e-439d-806b-55aac4cd84fd', variable: 'FTP_IP')
				]) {
					sh 'curl -sS -T ${TEMP_DIR}/${RELEASE_NAME}.img.xz -u ${FTP_USERNAME}:${FTP_PASSWORD} ftp://${FTP_IP}/data/pi-protect/'
				}
			}
		}
		stage("Check") {
			steps {
				sh 'test -e ${TEMP_DIR}/${RELEASE_NAME}.img.xz && sudo mv ${TEMP_DIR}/${RELEASE_NAME}.img.xz ${TEMP_DIR}/${RELEASE_NAME}.img.xz.orig'
				sh 'wget -q https://mechatrax.com/data/pi-protect/${RELEASE_NAME}.img.xz -P ${TEMP_DIR}'
				sh 'sha256sum -c ${TEMP_DIR}/${SUM_FILE}'
				sh 'sudo rm -vf ${TEMP_DIR}/${RELEASE_NAME}.img.xz ${TEMP_DIR}/${RELEASE_NAME}.img.xz.orig ${TEMP_DIR}/${SUM_FILE}'
			}
		}
	}
	post {
		success {
			zulipSend message: "✔ Pi-protect の SD イメージ ${RELEASE_NAME} のリリースに成功しました", stream: "${MAIN_STREAM}"
		}
		failure {
			zulipSend message: "❌ Pi-protect の SD イメージ ${RELEASE_NAME} のリリースに失敗しました", stream: "${MAIN_STREAM}"
		}
	}
}
