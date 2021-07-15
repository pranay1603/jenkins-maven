pipeline {
    agent { label 'mydocker'}
    stages {
        stage('pull from git') {
            step {
                 git 'https://github.com/pranay1603/jenkins-maven.git'
            } 
        }
        stage('test image nd creating package') {
            step {
                sh 'mvn package'
            }
        }
        stage('archive artifact') {
            step {
               archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
        stage('creating graph') {
            step {
                junit 'target/surefire-reports/*.xml'
            }
        }
    }
}