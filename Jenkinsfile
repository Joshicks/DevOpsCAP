pipeline {
    agent any
    tools {nodejs "node19"}
    stages {
        stage('Build Frontend Web') {
            steps {
                echo 'Building Frontend Angular'
                dir ('myangular/'){
                    sh 'npm -version'
                    sh 'node -v'
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
