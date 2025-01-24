pipeline{
    agent any
    tools{
        maven 'Maven3.9.9'
    }
    stages{
        stage("A"){
            steps{
                echo "========executing A========"
                sh 'mvn clean install'
            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
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
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}