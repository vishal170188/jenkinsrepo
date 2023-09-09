pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'master']], extensions: [], 
                userRemoteConfigs: [[url: 'https://github.com/Kaleakash/python_jenkins_file.git']]])
            }
        }
        stage('Build') {
            steps {
                git branch: 'master', url: 'https://github.com/Kaleakash/python_jenkins_file.git'
                sh 'python3 ops.py'
                //bat 'python ops.py'
            }
        }
        stage('Test') {
            steps {
                sh 'python3 -m pytest'
                //bat 'python -m pytest'
            }
        }
    }
  post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'Example : if the Pipeline was previously failing but is now successful'
        }
    }
}
