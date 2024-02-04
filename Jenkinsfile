pipeline {
    agent {
        node {
            label 'workstation'
        } 
    }
    environment {
        // using the envirnoment varibales here
        PackageVersion = ''
    }
    stages {
        stage("Read JSON File"){
            steps{
                script {
                    def Package_version = readJSON file: 'package.json'
                    PackageVersion = Package_version.version
                }
            }
        }
        stage('Build') {
            steps {
                // Add build steps here
                sh """
                    echo Building the build ${PackageVersion}
                    """ 
            }
        }
        stage('Test') {
            steps {
                // Add test steps here
                sh 'echo "Testing..."'
            }
        }
        stage('Deploy') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
            }
            steps {
                // Add deploy steps here
                sh 'echo "Deploying..."'
            }
        }
        stage('release') {
            steps {
                // Add release steps here
                sh 'echo "releasing the application..."'
            }
        }
        
    }
    post {
        always {
            echo "pipline is running...."
        }
        failure {
            echo "pipline is failure..."
        }
        success {
            echo "pipline is success...party..ledha..pushpa.."
        }
    }
}
