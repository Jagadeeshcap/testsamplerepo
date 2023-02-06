pipeline {

  agent any

  environment {
    DOCKERHUB_CREDENTIALS=credentials('TestDocker') // Create a credentials in jenkins using your dockerhub username and token from https://hub.docker.com/settings/security
  }


  stages {

    stage("Git Checkout") {
      steps {
        script {
           sh "git clone https://github.com/DashrathMundkar/cicd-java-maven-project.git"
        }
      }
    }

    stage("Maven Build") {
      steps {
        script {
          sh "mvn clean install -T 1C" // -T 1C is to make build faster using multithreading
        }
      }
    }

    stage("Build & Push Docker Image") {
      steps {
        script {
          sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
          sh "docker build -t dash18/cicd-java-maven ."
          sh "docker push dash18/cicd-java-maven"
        }
      }
    }
  post {
    always {
      script {
        if (currentBuild.currentResult == 'FAILURE') {
          step([$class: 'Mailer', notifyEveryUnstableBuild: true, recipients: "Test@test.com", sendToIndividuals: true])
        }
      }
    }
  }
}
