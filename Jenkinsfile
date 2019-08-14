//declarative pipeline
pipeline {
    agent any 

    stages {
        stage('\u26F9 Unit Test'){
            steps{
                sh "echo  I am stage: Unit Test"
                sh "./gradlew clean build"
            }
        }
        
        stage('\u261D Api Test'){
            steps{
                sh 'echo "I am stage: Api Test"'
            }
        }

        stage('\u270A Build jar'){
            steps{
                sh "./gradlew -x jar build"
            }
        }

        stage('\u270D Build image') {
            steps{
                sh 'echo "I am stage: Build image"'
                sh "docker build -t api-demo:v${env.BUILD_NUMBER} ."
            }
        } 

        stage('\u26F1  Deploy') {
            steps{
                sh 'echo "-----Deploy stage-----"'
                sh "docker run -d --name api-container -p 8080:8080 api-demo:v${env.BUILD_NUMBER}"
            }
        }         
    }   
}
