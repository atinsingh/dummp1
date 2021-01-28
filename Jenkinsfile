node {
    def MAVEN_HOME = tool 'm3';
    stage('Checkout SCM') {
        git branch: 'master', url: 'https://github.com/atinsingh/dummp1.git'
    }
    stage('Compile ') {
        withMaven(jdk: 'jdk8', maven: 'm3') {
           sh '${MAVEN_HOME}/bin/mvn compile'
         }
    }
    stage('Unit Test') {
        withMaven(jdk: 'jdk8', maven: 'm3') {
           sh '${MAVEN_HOME}/bin/mvn Test'
       }
    }
    stage('Publish Test Result') {
        junit '**/*.xml'
    }
    stage('Package') {
        withMaven(jdk: 'jdk8', maven: 'm3') {
          sh '${MAVEN_HOME}/bin/m package'
        }
    }
    stage('Publish Artifact') {
        archiveArtifacts artifacts: '**/*.jar', followSymlinks: false
    }
}
