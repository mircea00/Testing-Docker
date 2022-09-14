pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
                docker { image 'maven:3.8.1-adoptopenjdk-11' }
            }
            steps {
                sh 'mvn --version'
            }
        }
    }
    post {
        success {
            agent any
            echo '-----------------Deleting workspace--------------'
                cleanWs(cleanWhenNotBuilt: false,
                    deleteDirs: true,
                    disableDeferredWipeout: true,
                    notFailBuild: true,
                    patterns: [[pattern: '*', type: 'INCLUDE'],
                               [pattern: '.propsfile', type: 'EXCLUDE']])
        }    
    }
}
