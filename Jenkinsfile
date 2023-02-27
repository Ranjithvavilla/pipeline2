pipeline {
  agent any
  tools {
    maven 'MAVEN_HOME' 
  }
  stages {
    stage ('Build') {
      steps {
        bat 'mvn clean package'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat9(credentialsId: 'be428aba-3e90-43e9-b232-dea660d457c0', path: '', url: 'http://localhost:1080')], contextPath: '/pipeline', onFailure: false, war: '**/*.war'
        }
      }
    }
  }
}
