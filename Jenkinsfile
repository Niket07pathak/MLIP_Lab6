pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat '''
                echo In C or Java, we can compile our program in this step
                echo In Python, we can build our package here or skip this step
                '''
            }
        }
        stage('Test') {
            steps {
                bat '''
                echo Test Step: Running pytest on Windows system
                call mlip\Scripts\activate
                pytest --maxfail=1 --disable-warnings
                call mlip\Scripts\deactivate
                '''
            }
        }
        stage('Deploy') {
            steps {
                bat '''
                echo In this step, we deploy our project
                echo Depending on the context, we may publish the project artifact or upload pickle files
                '''
            }
        }
    }
}
