pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'start dotnet build eShopOnWeb.sln'
      }
    }

    stage('Tests') {
      parallel {
        stage('Unit') {
          steps {
            sh 'start dotnet test tests/UnitTests'
          }
        }

        stage('Integration') {
          steps {
            sh 'start dotnet test tests/IntegrationTests'
          }
        }

        stage('Functional') {
          steps {
            sh 'start dotnet test tests/FunctionalTests'
          }
        }

      }
    }

    stage('Deployment') {
      steps {
        sh 'start dotnet publish eShopOnWeb.sln -o /var/aspnet'
      }
    }

  }
}