pipeline {
    agent{
            label "master"
        }
        tools {
            maven 'maven'
            jdk 'jdk8'
        }
    stages {

        stage('Run Stage') {
            steps {
                echo 'Running the application...'
                sh 'java -jar target/*.jar'
            }
        }
    }
    post {
        success{
        echo "Running stage successful"
        }
        failure{
        echo "Running stage failed"
        }
    }
}
