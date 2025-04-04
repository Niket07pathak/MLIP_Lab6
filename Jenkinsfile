pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''#!/bin/bash
                echo 'In C or Java, we can compile our program in this step'
                echo 'In Python, we can build our package here or skip this step'
                '''
            }
        }
        stage('Test') {
            steps {
                script {
                    if (isUnix()) {
                        // For Linux/Mac systems
                        sh '''
                        echo "Test Step: Running pytest on Unix system"
                        source mlip/bin/activate
                        pytest --maxfail=1 --disable-warnings
                        deactivate
                        '''
                    } else {
                        // For Windows systems
                        bat '''
                        echo Test Step: Running pytest on Windows system
                        call mlip\\Scripts\\activate
                        pytest --maxfail=1 --disable-warnings
                        call mlip\\Scripts\\deactivate
                        '''
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'In this step, we deploy our porject'
                echo 'Depending on the context, we may publish the project artifact or upload pickle files'
            }
        }
    }
}
