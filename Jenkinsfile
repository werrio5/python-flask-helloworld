pipeline {
    //https://gist.github.com/bvis/68f3ab6946134f7379c80f1a9132057a
    //https://www.jenkins.io/doc/book/pipeline/syntax/
    
    environment {
        TEST_PREFIX = "test-IMAGE"
        TEST_IMAGE = "${env.TEST_PREFIX}:${env.BUILD_NUMBER}"
        TEST_CONTAINER = "${env.TEST_PREFIX}-${env.BUILD_NUMBER}"
        REGISTRY_ADDRESS = "my.registry.address.com"

        SLACK_CHANNEL = "#deployment-notifications"
        SLACK_TEAM_DOMAIN = "MY-SLACK-TEAM"
        SLACK_TOKEN = credentials("slack_token")
        DEPLOY_URL = "https://deployment.example.com/"

        COMPOSE_FILE = "docker-compose.yml"
        REGISTRY_AUTH = credentials("docker-registry")
        STACK_PREFIX = "my-project-stack-name"
    }

    // agent any
    agent {
        docker {
            args '-v ./:/app -p 80:80'
            image 'jazzdd/alpine-flask'
            label 'flask-helloworld'
        }
    }

    stages {
        // stage('Build') {
        //     steps {
        //         sh "docker-compose up --build"
        //     }
        // }
        stage('Test') {
            steps {
                dir('/app') {                    
                    sh 'python3 -m unittest discover -vvv'
                }               
            }
        }
        stage('Deploy') {
            steps {
                echo '(not) Deploying....'
            }
        }
    }
}

// node {    
//       def app     
//       stage('Clone repository') {               
             
//             checkout scm    
//       }     
//       stage('Build image') {         
       
//             app = docker.build("brandonjones085/test")    
//        }     
//       stage('Test image') {           
//             app.inside {            
             
//              sh 'echo "Tests passed"'        
//             }    
//         }     
//        stage('Push image') {
//                                                   docker.withRegistry('https://registry.hub.docker.com', 'git') {            
//        app.push("${env.BUILD_NUMBER}")            
//        app.push("latest")        
//               }    
//            }
//         }