pipeline {
  agent any
  tools {
    maven 'maven'
  }

  stages {
    stage('build') {
      steps {
        sh 
        mvn 
        '''pwd
ls
date'''
      }
    }

    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            echo 'Testing stage'
            sh 'mvn test'

          }
        }

        stage('Integration testing') {
          steps {
            echo 'Integration testing'
          }
        }

      }
    }

    stage('Sonar') {
      steps {
        echo 'code quality'
      }
    }

    stage('deploy') {
      steps {
        echo 'deployment'
        sh 'mvn install'
        deploy adapters: [tomcat9(path: '', url: 'http://127.0.0.1:8088')], contextPath: '/app', onFailure: false, war: '**/*.war'
      }
    }
  }
}
