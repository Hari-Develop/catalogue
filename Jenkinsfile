pipeline {

    agent {
        node {
            label 'Jenkins_agent'
        } 
    }


    environment {
        // using the environment variables here
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


        stage('installing dependencies') {
            steps {
                // Add npm steps here
                sh """
                    echo installing npm dependencies 
                    pwd
                    npm install
                    ls -la
                    zip -r catalogue.zip ./* -x jenkinsfile -x ".git" "Jenkinsfile"
                    ls -a
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
            echo "pipeline is running...."
            deleteDir()
        }
        failure {
            echo "pipeline is failure..."
        }
        success {
            echo "pipeline is success...party..ledha..pushpa.."
        }
    }


} 