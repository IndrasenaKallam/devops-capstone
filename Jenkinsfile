pipeline {
    environment {
    registry = "indrasena919/devops-capstone"
    registryCredential = 'Docker'
    }
    
    agent any
    stages {
        
        stage ('Cloning Git') {
            steps {
                sh 'git clone https://github.com/IndrasenaKallam/devops-capstone.git'
            }
        }
        
        stage ('Lint HTML') {
            steps {
                sh 'tidy -q -e *.html'
            }
        }
 

        stage('Building image') {
            steps {
                script {
                    sh 'docker build --tag=$registry .'
                }
            }
        }

        stage('Deploy Image') {
            steps {
                script {
                    withDockerRegistry([ credentialsId: "$registryCredential", url: "" ]) {
                    sh 'docker push $registry'
                    }
                }
            }
        }

    }
}
