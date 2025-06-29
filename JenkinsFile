pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Restore the project') {
            steps {
                bat 'dotnet restore Horizons.sln'
            }
        }

        stage('Build the project') {
            steps {
                bat 'dotnet build Horizons.sln --no-restore --configuration Debug'
            }
        }

        stage('Test the project') {
            steps {
                bat 'dotnet test Horizons.Tests.Unit/Horizons.Tests.Unit.csproj --no-build --verbosity normal'
                bat 'dotnet test Horizons.Tests.Integration/Horizons.Tests.Integration.csproj --no-build --verbosity normal'
            }
        }
    }
}