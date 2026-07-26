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
                sudo mkdir -p /opt/staging
                sudo cp -r * /opt/staging/
                cd /opt/staging
                nohup python3 app.py > app.log 2>&1 &
                echo "Application deployed and started in staging."
                '''
                }
        }
    }
}
