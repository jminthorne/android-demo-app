node{
    stage('Checkout'){
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'gl-ssh-key', url: 'https://gitlab.com/axcelinno/simple-web-app-demo.git']]])
    }
    
    stage('Build') {
        slackSend channel: '#development-demo', color: 'warning', message: "Build ${env.JOB_NAME} ${env.BUILD_NUMBER} has started! Additional information can be found (<${env.BUILD_URL}|here>)", notifyCommitters: true
        slackUserIdsFromCommitters()
    }

    stage('Send APK') {
        slackSend channel: '#development-demo', color: 'good', message: "Build was a success! The APK: example-1.0.apk for build: ${env.JOB_NAME} ${env.BUILD_NUMBER} can be downloaded (<http://sonatype-nexus-devops.apps.lab.ocp4.axcelinno.cloud/repository/Maven-Decision_Manager/com/example/1.0/example-1.0.apk|here>). Additional information can be found (<${env.BUILD_URL}|here>)."
    }
}    