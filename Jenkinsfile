node {
    // Get Artifactory server instance, defined in the Artifactory Plugin administration page.
    //def server = Artifactory.server "SERVER_ID"
    // Create an Artifactory Gradle instance.
    //def rtGradle = Artifactory.newGradleBuild()
    //def buildInfo

    stage('Clone sources') {
        git url: 'https://gitlab.com/axcelinno/android-demo-app.git'
    }


    stage('Gradle build') {
        buildInfo = rtGradle.run buildFile: 'build.gradle', tasks: 'clean build'
    }

    stage('Publish build info') {
        server.publishBuildInfo buildInfo
    }
}