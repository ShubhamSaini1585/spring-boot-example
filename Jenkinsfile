pipeline {
    agent {
        label 'slave-1'
    }
    stages {
        stage("Production") {
            steps {
                //echo "Production branch"
                sh "mvn clean package"
            }
        }
    }
    post {
        always{
                    mail to: 'shubham.saini@knoldus.com',
        			subject: "Pipeline: ${currentBuild.fullDisplayName} is ${currentBuild.currentResult}",
        			body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}"
                }
        success {
            echo "Packaging successful"
        }
        failure {
            echo "Packaging unsuccessful"
        }
    }
}