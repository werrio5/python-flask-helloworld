pipeline {
    //https://gist.github.com/bvis/68f3ab6946134f7379c80f1a9132057a
    //https://www.jenkins.io/doc/book/pipeline/syntax/

    //agent any
    agent {
        docker {
            args '-v /var/jenkins_home/workspace/python-flask-helloworld-test/app:/app -p 80:80'
            image 'jazzdd/alpine-flask'
        }
    }

    stages {
        // stage('Build') {
        //     steps {
        //         script {
        //             def app = docker.build("jazzdd/alpine-flask", "-v /app:/app -p 80:80")
        //         }                
        //     }
        // }
        stage('Test') {
            steps {
                sh 'python3 -m unittest discover -vvv'                         
            }
        }
        stage('Deploy') {
            steps {
                echo '(not) Deploying....'
            }
        }
    }
    // post {
    //     always {            
    //         sh 'docker stop $(docker ps -a -q)'
    //         sh 'docker rm $(docker ps -a -q)'
    //         sh 'docker rmi $(docker ps -a -q)'            
    //     }
    // }
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