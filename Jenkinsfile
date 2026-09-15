pipeline{
    agent{
        docker{
             image 'python:3.13-alpine'
             args '-u root'

        } 
        
    }
    stages{
        stage('checkout'){
            steps{
                checkout scm
            }
        }
        stage('install dependency'){
            steps{
                 sh 'pip install --target=/tmp/python-packages -r requirements.txt'
            }
        }
        stage('run application'){
            steps{
                sh 'PYTHONPATH=/tmp/python-packages python app.py'
            }
        }
        stage('test application'){
            steps{
                sh 'PYTHONPATH=/tmp/python-packages python -m pytest '
            }
        }
    }
    post{
        success{
            echo 'accepted'
        }
        failure{
            echo 'rejected'
        }
    }
}