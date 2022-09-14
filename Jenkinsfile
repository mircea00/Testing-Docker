pipeline {
    agent {
     docker : 'node-10.14.0-alpine'
}
    stages {
        stage('Build') {
            steps {
                script {
                sh 'cd ..'
                sh 'ls'
                sh 'ls -l /var/jenkins_home/workspace'
                sh 'ls -l $WORKSPACE'
                sh 'ls -l /usr/bin'
                }
            }
        }
    }
    post {
        success {
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
