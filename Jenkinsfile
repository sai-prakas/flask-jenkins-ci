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
            apt update
            apt install -y python3-venv python3-pip
            pip3 install --upgrade pip
            pip3 install pytest
        '''
    }
}





        stage('Run Tests') {
    steps {
        sh '''
            python3 -m pytest
        '''
    }
}

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }
}