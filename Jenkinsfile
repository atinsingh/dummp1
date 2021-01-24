node {
    
    stage('Checkout SCM') {
        git branch: 'dev', credentialsId: 'githubs', url: 'https://github.com/atinsingh/dummp1.git'
    }
    stage('Compile ') {
        withMaven(jdk: 'jdk8', maven: 'm363') {
         //sh 'mvn compile'
           sh 'echo hello'
           sleep 10
        }
    }
    stage('Unit Test') {
        withMaven(jdk: 'jdk8', maven: 'm363') {
         //sh 'mvn Test'
           sh 'echo test'
           sleep 10
        }
    }
    stage('Publish Test Result') {
        //junit '**/*.xml'
        sh 'echo result'
        sleep 5
    }
    stage('Package') {
        withMaven(jdk: 'jdk8', maven: 'm363') {
         //sh 'mvn package'
          sh 'echo package'
        }
    }
    stage('Update Slack') {
        slackSend channel: 'devops-nov-2020', color: 'red', message: 'Build Success Job '${JOB_NAME}' '${BUILD_NUMBER}''
    }
    stage('Publish Artifact') {
        //archiveArtifacts artifacts: '**/*.jar', followSymlinks: false
        mail bcc: '', body: '', cc: '', from: '', replyTo: '', subject: '', to: 'atin.singh@gmail.com'
    }
}
