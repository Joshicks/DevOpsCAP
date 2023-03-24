pipeline {
    agent any
    tools {nodejs "node16"}
    stages {
        stage('Build Frontend Web') {
            steps {
                echo 'Building Frontend Angular'
                dir ('myangular/'){
                    bat 'npm -version'
                    bat 'node -v'
                    bat 'npm install'
                    bat 'npm run build'
                }
            }
        }
        stage('Deploy Frontend Web') {
            steps {
                echo 'Deploy Frontend Angular'
                bat 'docker build -t frontalex .'
                bat 'docker run -d -p 9090:80 frontalex'
            }
        }
    }
    post { 
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
