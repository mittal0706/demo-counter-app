pipeline{
    
    agent any
        stages {
           stage('Git Checkout'){ 
            steps{
                script{  
                    git branch: 'main', url: 'https://github.com/mittal0706/demo-counter-app.git'
                }
            }
        }
            stage('Unit Testing'){
                agent {
                    docker { image 'maven' }
                }
                steps{   
                    script{     
                    sh 'mvn test'
                }
            }
        }
            stage('Integration Testing'){
                agent {
                    docker { image 'maven' }
                }
                steps{
                    script{ 
                    sh 'mvn verify -DskipUnitTests'
                    }
                }
            }
            stage('maven build'){
                agent {
                    docker { image 'maven' }
                }
                steps{
                    script{ 
                    sh 'mvn clean install'
                    }
                }
            }          
   }
        
    stage('static code analysis') {
        steps{
            script{
                withSonarQubeEnv(credentialsId: 'sonar-api'){
                    sh 'mvn clean package sonar:sonar'
                }
            }
        }
    }

    stage('Quality Gate status'){
        steps{
            script{
                waitForQualityGate abortPipeline: false, credentialsId: 'sonar-api'
            }
        }
    }
    
}

