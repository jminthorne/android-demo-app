node('jenkins-slave-gradle6'){
    stage('Checkout'){
        checkout([$class: 'GitSCM', branches: [[name: '*/v2']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'gl-ssh-key', url: 'https://gitlab.com/axcelinno/android-demo-app.git']]])
        sh 'pwd'
        sh 'ls -l ./build'
    }

    stage('Build') {
        slackSend channel: '#development-demo', color: 'warning', message: "Build ${env.JOB_NAME} ${env.BUILD_NUMBER} has started! Additional information can be found (<${env.BUILD_URL}|here>)", notifyCommitters: true
        slackUserIdsFromCommitters()
        archiveArtifacts 'build/app-debug.apk'
         
    }
    
      stage('Send APK') {
        slackSend channel: '#development-demo', color: 'good', message: "Build was a success! The APK for build: ${env.JOB_NAME} ${env.BUILD_NUMBER} can be downloaded (<${env.BUILD_URL}artifact/build|here>)."
    }
}