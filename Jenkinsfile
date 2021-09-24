@Library("Shared-library") _
currentBuild.displayName = "${currentBuild.projectName}#${currentBuild.number}"
pipeline {
    agent any 
    tools {
        // Note: this should match with the tool name configured in your jenkins instance (JENKINS_URL/configureTools/)
        nodejs "node"
    }
        stages {
            stage ("git code checkout"){
            steps{
                echo "get source code"
                git changelog: false, credentialsId: 'git_creds', poll: false, url: 'https://github.com/jinjadarkwebjinja/hello-world-java.git'
                echo 'scm is done guys!'
            }
        }
            stage ("Build"){
            steps{
                echo "Build the app"
                helloWorld()
            }
            }
            stage("Env Build Number"){
            steps{
                echo "The build number is ${env.BUILD_NUMBER}"
                echo "The job name is ${env.JOB_NAME}"
                echo "The Jenkins URL is ${env.JENKINS_URL}"
                echo "The Build URL is ${env.BUILD_URL}"
               echo "The GIt Branch URL is ${env.GIT_BRANCH}"
               echo "The Jenkins Veedu URL is ${env.JENKINS_HOME}"
               echo "The Jenkins Workspace is ${env.WORKSPACE}"
            }
            }
            stage('Build Status Through Email Notification'){
            steps{
            mail bcc: 'sridhar.vimala@infosys.com', body: ''' Thanks,
Sangi Mangi & Mangi Sangi''', cc: 'jinjajenkinsuser@gmail.com', from: '', replyTo: '', subject: "${env.JOB_NAME}" , to: ''
        }
}
        }
}
