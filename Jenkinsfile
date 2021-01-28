node {
    def MAVEN_HOME = tool 'm3';
    stage('Checkout SCM') {
        sh 'export PATH=$PATH:${MAVEN_HOME}/bin'
        git branch: 'master', url: 'https://github.com/atinsingh/dummp1.git'
    }
    stage('Compile ') {
        withMaven(jdk: 'jdk8', maven: 'm3') {
           sh "mvn compile"
         }
    }
    stage('Unit Test') {
        withMaven(jdk: 'jdk8', maven: 'm3') {
           sh 'mvn test'
       }
    }
    stage('Publish Test Result') {
        junit '**/*.xml'
    }
    stage('Package') {
        withMaven(jdk: 'jdk8', maven: 'm3') {
          sh 'mvn package'
        }
    }
    stage('Publish Artifact') {
        archiveArtifacts artifacts: '**/*.jar', followSymlinks: false
    }
}
