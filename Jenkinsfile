pipeline {
    agent{
            label "slave-2"
        }
        tools {
            maven 'maven'
            jdk 'jdk11'
        }

    stages{
        stage("cleaning"){
            steps{
                sh "mvn clean"
                sh 'ls'
            }
        }
        stage("compile"){
            when{
                branch 'development'
            }
            steps{
                sh "mvn compile"
            }
        }
        stage("testing"){
            steps{
                sh "mvn test"
                sh 'echo "Listing the files in the current dir"'
                sh "ls"
            }
        }
        stage("packaging"){
            when{
                expression { BRANCH_NAME ==~ /(development)/ }
            }
            steps{
                sh 'mvn package'
            }
        }
        stage("deploying"){
            when{
                branch 'production'
            }
            steps{
                sh "ls"
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
