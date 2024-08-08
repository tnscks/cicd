peline {
  agent any

  triggers {
    pollSCM('* * * * *')
  }
  stages {
    stage('Checkout') {
      steps {
        git branch: 'main',
	url: 'https://github.com/tnscks/cicd.git'
      }
    }
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }
    stage('Deploy') {
      steps {
        deploy adapters: [tomcat9(credentialsId: 'admin', url: 'http://192.168.56.102:8080/' )], contextPath: null, war: 'path/to/war'
      }
    }
  }
}
