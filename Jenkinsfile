pipeline {
    agent any
    stages {

        stage('Build with Maven') {
            steps {
                echo 'Building with Maven:'
                sh 'mvn mvn clean compile'
            }
            post{
                success{
                    echo 'Build Succesful!'
                }
                failure{
                    // mail to: morisfrances2@gmail.com, subject: "${env.JOB_NAME} failed"
                    error('Build unsuccesful; Deployment will not be carried out') 
                }
            } 

        }
        stage('Run Unit Tests with Maven') {
            steps {
                echo 'Running unit tests:'
                echo 'TO BE IMPLEMENTED'
                // sh 'mvn test'
            }

        }
        stage('Run Selenium UI Tests with Maven') {
            steps {
                echo 'Running Selenium UI Tests:'
                echo 'TO BE IMPLEMENTED'
                // sh 'mvn test'
            }

        }

        stage('Deploy to Wildfly') {
            steps {
                echo 'Build and Tests succesful; Deploying:'
                sh 'mvn wildfly:deploy'
            }
        }
    }
    post{
        success{
            echo "Finished pipeline for commit ${env.GIT_COMMIT}"
            archiveArtifacts(artifacts: 'target/*.war', fingerprint: true)
            // echo 'Build and Tests succesful; Deploying to Wildfly Server:'
            // sh 'mvn wildfly:deploy'
        }
        failure{
            // mail to: morisfrances2@gmail.com, subject: "${env.JOB_NAME} failed"
            echo 'Build or Test unsuccesful; Deployment will not be carried out'
        }
    }
}
