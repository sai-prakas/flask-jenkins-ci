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
        withCredentials([string(credentialsId: 'SUDO_PASSWORD', variable: 'SUDO_PASS')]) {
            sh '''
                echo $SUDO_PASS | sudo -S apt update
                sudo apt install -y python3-venv python3-pip
                pip3 install --upgrade pip
                pip3 install pytest
            '''
        }
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