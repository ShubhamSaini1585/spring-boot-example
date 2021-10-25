pipeline{
    agent{
        label "slave-3"
    }
    tools { 
        maven 'maven' 
        jdk 'jdk 11'
    }
    stages{
        stage("Cleaning"){
            steps{
                sh "mvn clean"
                sh "ls"
            }
        }
        stage("Compile"){
            When{
                branch 'development'
            }
            steps{
                sh "mvn compile"
            }
        }
                stage("testing"){
            steps{
                //sh "mvn test"
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

    }
    post{
        always{
                    mail to: 'shubham.saini@knoldus.com',
        			subject: "Pipeline: ${currentBuild.fullDisplayName} is ${currentBuild.currentResult}",
        			body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}"
                }
        success{
            echo "Pipeline Executed Successfully"
        }
        failure{
            echo "Pipeline Execution Failed"
        }
    }
}
