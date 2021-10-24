pipeline {
    agent{
            label "slave-2"
        }
        tools {
            maven 'maven'
            // jdk 'jdk8'
        }

    stages {

        stage('Testing') {
            steps {
                echo 'Testing the Application...'
                sh "mvn clean test"

            }
        }
    }
    post {
        //always{
          //          mail to: 'shubham.saini@knoldus.com',
        	//		subject: "Pipeline: ${currentBuild.fullDisplayName} is ${currentBuild.currentResult}",
        	//		body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}"
             //   }
        success{
        echo "Testing stage successful"
        }
        failure{
        echo "Testing stage failed"
        }
    }
}