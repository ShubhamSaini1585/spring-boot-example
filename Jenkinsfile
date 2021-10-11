pipeline {
    agent none
    stages {
        stage {
            steps {
                //echo "Production branch"
                sh 'mvn clean package'
            }
        }
    }
    post {
        success {
            echo "Packaging successful"
        }
        failure {
            echo "Packaging unsuccessful"
        }
    }
}