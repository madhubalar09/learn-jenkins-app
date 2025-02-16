pipeline {
    agent any

    stages {
        stage('build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
               sh '''
               ls -la
               node --version
               npm --version
               npm ci
               npm run build
               '''
            }
        }
        stage ('test'){
           agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
           }
            steps {
               sh ''' 
               pwd
               ls /learn-jenkins-app/build/index.html
               npm test
               '''
            }
        }
    }
}
