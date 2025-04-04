pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                bat '''
                echo "Setting up Python virtual environment..."
                python -m venv .venv
                call .venv\\Scripts\\activate
                pip install --upgrade pip
                pip install pytest
                pip install -r requirements.txt
                '''
            }
        }
        stage('Build') {
            steps {
                bat '''
                call .venv\\Scripts\\activate
                echo "In C or Java, we can compile our program in this step"
                echo "In Python, we can build our package here or skip this step"
                '''
            }
        }
        stage('Test') {
            steps {
                bat '''
                call .venv\\Scripts\\activate
                echo "Test Step: Running pytest..."
                pytest . --junitxml=report.xml
                echo "Test Completed"
                '''
            }
        }
        stage('Deploy') {
            steps {
                bat '''
                call .venv\\Scripts\\activate
                echo "In this step, we deploy our project"
                echo "Depending on the context, we may publish the project artifact or upload pickle files"
                '''
            }
        }
    }
}