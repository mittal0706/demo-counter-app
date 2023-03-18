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
            
            steps{
                
                script{
                    
                    sh 'mvn test'
                }
            }
        }
        
   }
        
}
