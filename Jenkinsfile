pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', 
                    credentialsId: 'da8500f6-a482-4351-aec1-3c9eba997e36', 
                    url: 'https://github.com/sai-prakas/flask-jenkins-ci.git'
            }
        }
        stage('Install Dependencies') {
    steps {
        sh '''
        python3 -m venv venv
        source venv/bin/activate
        pip install --upgrade pip
        pip install -r requirements.txt
        '''
    }
}

        stage('Run Tests') {
            steps {
                sh 'pytest'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }
}