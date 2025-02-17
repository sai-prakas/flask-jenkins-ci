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
                echo "Installing Python dependencies from requirements.txt (if present)..."
                // Check if requirements.txt exists; if yes, install using pip.
                sh '''
                  if [ -f requirements.txt ]; then
                    pip install -r requirements.txt
                  else
                    echo "No requirements.txt file found. Skipping dependency installation."
                  fi
                '''
            }
        }
        stage('Run Tests') {
            steps {
                echo "Running tests with pytest..."
                // Check if tests exist (e.g., a tests/ directory or pytest.ini); if yes, run pytest.
                sh '''
                  if [ -d tests ] || [ -f pytest.ini ]; then
                    pytest
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
                // For example: sh 'python deploy.py'
            }
        }
    }
    
    post {
        always {
            echo "Pipeline finished."
        }
    }
}
