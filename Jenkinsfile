pipeline {
  agent any

  tools {
    maven 'Maven-3'
  }

  environment {
    APP_NAME = "DemoApp"
  }

  stages {

    stage('Checkout') {
  steps {
    git branch: 'main', url: 'https://github.com/Liki-git/jenkins-demo.git'
  }
}

    }

    stage('Build') {
      steps {
        bat 'mvn clean compile'
      }
    }

    stage('Test') {
      steps {
        bat 'mvn test'
      }
      post {
        always {
          junit '**/target/surefire-reports/*.xml'
        }
      }
    }

    stage('Package') {
      steps {
        bat 'mvn package'
      }
    }

    stage('Deploy') {
      steps {
        echo "Deploying ${APP_NAME}"
      }
    }
  }

  post {
    success {
      echo 'Pipeline Succeeded'
    }
    failure {
      echo 'Pipeline Failed'
    }
  }
}
