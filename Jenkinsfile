pipeline {
  agent {
    docker {
      image 'maven:3-alpine'
      args '-v /root/.m2:/root/.m2'
    }

  }
  stages {
    stage('Build') {
      steps {
        git 'https://github.com/LUFFY-lucy/simple-java-maven-app'
        sh 'mvn -B -DskipTests clean package'
      }
    }
    stage('test') {
      steps {
        sh 'mvn test'
      }
    }
    stage('deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        input 'deliver Done'
      }
    }
  }
}