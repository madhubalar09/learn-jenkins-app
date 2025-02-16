pipeline {
    agent any

    environment{
            path = 'sh 'pwd''
    }

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
               ls $path/build/index.html
               npm test
               '''
            }
        }
    }
}
