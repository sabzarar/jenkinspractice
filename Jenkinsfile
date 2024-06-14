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
