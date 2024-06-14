pipeline{
    agent any
    tools {
        maven 'maven'
    }
    stages{
        stage("Build"){
            steps{

                echo "========executing Build========"
                sh 'mvn --version'
            }
           
        }
         stage("Test"){
            steps{

                echo "========executing Testing========"
                 sh 'mvn test'
            }
           
        }
         stage("Sonar"){
            steps{

                echo "========executing Code Quality========"
               
            }
           
        }
         stage("Deploy"){
            steps{

                echo "========executing Deploy========"
                sh 'mvn package'
                deploy adapters: [tomcat9(path: '', url: 'http://127.0.0.1:8088')], contextPath: '/app', onFailure: false, war: '**/*.war'
                
            }
           
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
