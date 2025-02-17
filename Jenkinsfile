pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Install Dependencies') {
            steps {
                echo "Creating virtual environment..."
                // Create a virtual environment in the workspace directory
                sh 'python3 -m venv venv'
                
                echo "Upgrading pip and installing dependencies..."
                // Upgrade pip and install dependencies from requirements.txt (if present)
                sh '''
                  venv/bin/pip install --upgrade pip
                  if [ -f requirements.txt ]; then
                    venv/bin/pip install -r requirements.txt
                  else
                    echo "No requirements.txt found. Skipping dependency installation."
                  fi
                '''
            }
        }
        stage('Run Tests') {
            steps {
                echo "Running tests with pytest..."
                // Run tests using the virtual environment's pytest
                sh '''
                  if [ -d tests ] || [ -f pytest.ini ]; then
                    venv/bin/pytest
                  else
                    echo "No tests found. Skipping test stage."
                  fi
                '''
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying application..."
                // Insert your deployment commands here.
                // For example: sh 'venv/bin/python deploy.py'
            }
        }
    }
    
    post {
        always {
            echo "Pipeline finished."
        }
    }
}
