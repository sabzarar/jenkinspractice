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
               deploy adapters: [tomcat9(credentialsId: 'tomcatuser', path: '', url: '')], contextPath: '/app', onFailure: false, war: '**/*.war'
                
            }
            post{
       
                failure{
                    echo "========pipeline execution failed========"
                    def msg = "${buildStatus}: `${env.JOB_NAME}` #${env.BUILD_NUMBER}:\n${env.BUILD_URL}"

                    slackSend channel: 'jenkinspipeline', message: msg
                }
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
            slackSend channel: 'jenkinspipeline', message: 'build success with $BUILD_ID'
        }
        failure{
            echo "========pipeline execution failed========"
            slackSend channel: 'jenkinspipeline', message: 'ProjectA build failed with $BUILD_ID'
        }
    }
}
