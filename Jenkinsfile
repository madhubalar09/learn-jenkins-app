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
        environment{
            path = 'sh 'pwd''
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
