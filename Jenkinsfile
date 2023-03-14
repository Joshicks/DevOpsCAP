pipeline {
    agent any
    stages {
        stage('Build Frontend Web') {
            steps {
                echo 'Building Frontend Angular'
                dir ('myangular/'){
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        stage('Deploy Frontend Web') {
            steps {
                echo 'Deploy Frontend Angular'
                sh 'docker build -t frontalex .'
                sh 'docker run -d -p 9090:80 frontalex'
            }
        }
    }
    post { 
        always { 
            // deleteDir()
        }
        success {
            echo 'I succeeeded!'
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things were different before...'
        }
    }
}
