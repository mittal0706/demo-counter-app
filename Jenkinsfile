pipeline{
    
    agent none
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
                steps{
                    script{ 
                        sh 'mvn verify -DskipUnitTests'
                    }
                }
            }
                        
   }
        
}
