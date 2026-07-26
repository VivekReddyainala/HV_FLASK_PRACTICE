pipeline {
    agent any

    environment {
        MONGO_URI = 'mongodb://localhost:27017/test_student_db'
    }  

    stages {
        stage('Build') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh 'python3 -m pytest'
            }
        }

        stage('Deploy') {
            steps {
                    sh '''
                    mkdir -p /opt/staging
                    cp -rf * /opt/staging/
                    echo "Application deployed to staging."
                    '''
                }
        }
    }
}
