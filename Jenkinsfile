
pipeline {
    agent any
    stages {
        stage ("git clone") {
            steps {
                git credentialsId: 'github', url: 'https://github.com/tejesh555/helloworld.git'
            }    
        }

        stage ("checkout") {
            steps {
                script {
                    sh """ 
                        git checkout "${branch}" """
                }
            }
        }

        stage ("Build") {
            steps {
                script {
                   sh  "mvn clean install"
                }
            }
        }

        stage ("CD") {
            steps {
                script {
                    sh ""
                    //sh "ansible-playbook -i {{inventory_name}} playbook"
                }
            }
        }
        
        stage ("notify") {
            steps {
                emailext body: 'this is status of job "${BUILD_URL}"', subject: 'Job Status', to: 'tejesh2311@gmail.com'
            }
        }
    }
}