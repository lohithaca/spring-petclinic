pipeline{
    agent any
    tools{
        maven 'Maven3.9.9'
        sonarQubeScanner 'SonarQube Scanner'
    }
    environment {
        SONARQUBE_URL = 'http://localhost:7900/'
    }
    stages{
        stage("Build"){
            steps{
                echo "Building"
                sh 'mvn clean install'
            }
            post{
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
        stage("Test"){
            steps{
                sh "mvn test"
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    echo "Sonar Scan Running"
                    sh 'sonar-scanner -Dsonar.projectKey=my_project -Dsonar.sources=src'
                }
            }
        }
        stage("Code Coverage"){
            steps{
                echo "Generate Code Coverage Report"
                sh 'mvn jacoco:report'
            }
        }
        stage("Package and Archive"){
            steps{
                echo 'Archiving artifacts...'
                sh 'mvn package -DskipTests'
            }
        }
    }
    post{
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
