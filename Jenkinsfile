pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Restore Dependencies') {
            steps {
                echo 'Restoring .NET packages...'
                sh 'dotnet restore Homies.sln'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'dotnet build Homies.sln --configuration Release --no-restore /p:WarningLevel=0'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'dotnet test Homies.sln --configuration Release --no-build'
            }
        }
    }
}
