pipeline{
    agent{
        label "master"
    }
    tools { 
        maven 'maven' 
        jdk 'jdk 11'
    }
    stages{
        stage("building"){
            steps{
                sh "mvn clean package"
            }
        }

    }
    post{
        success{
            echo "Pipeline Executed Successfully"
        }
        failure{
            echo "Pipeline Execution Failed"
        }
    }
}