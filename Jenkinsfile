pipeline {
  agent any
  options {
      timestamps()
  }
  stages {
    stage('Git Clone') {
      steps {
        git branch: 'mavenWrapper', url: 'https://github.com/wonskarol/junit4.git'       
      }
    }
    stage("Build") {
      steps {
        sh "./mvnw clean"
        sh "./mvnw validate"
        sh "./mvnw compile"
      }
    }
    stage("Test") {
      steps {
        sh "./mvnw test"
        junit '**/target/surefire-reports/*.xml' 
      }
    }
  }
}
