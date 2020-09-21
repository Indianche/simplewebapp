
@Library('jenkins-shared-library@master') _

pipeline{
    agent {label 'java'}
    environment{
       PATH = "/usr/share/maven/bin:$PATH"
    }
    
    stages{
       
        stage('Git Checkout') {
            steps{
                gitCheckout(
                    branch: "master",
                    url: "https://github.com/Indianche/simplewebapp.git"
                )
            }
        }
        
        stage("maven build"){
            steps{
                mavenBuild()
            }   
        } 
         /*stage("Email"){
            steps{
                
                emailext (to: 'durgamsanthosh141@gmail.com', replyTo: 'durgamsanthosh141@gmail.com', subject: "Test Reports from - '${env.JOB_NAME}' ", 
                          body: readFile("target/surefire-reports/AppTest.txt"), mimeType: 'text/plain');
            }   
        } */
        
        
        stage("depploy"){
            steps{
                deploy( 
                    filepath: "target/java-tomcat-maven-example.war"
                      )
                 
                //step([$class: 'DockerComposeBuilder', dockerComposeFile: 'docker-compose.yml', option: [$class: 'StartAllServices'], useCustomDockerComposeFile: true])
            }   
        }
        
        
    }   
}
