pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                bat '''
                echo "Setting up Python virtual environment..."
                "C:\\Users\\n07pa\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m venv .venv
                call .venv\\Scripts\\activate
                "C:\\Users\\n07pa\\AppData\\Local\\Programs\\Python\\Python313\\python.exe" -m pip install --upgrade pip
                pip install pytest
                if exist requirements.txt pip install -r requirements.txt
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