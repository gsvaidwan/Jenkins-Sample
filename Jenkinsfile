pipeline{
    
    tools{
        maven 'mymaven'
    }
    
    agent any
    
    stages{
        stage('Clone the repo')
        {
            steps{
            git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
            }
        }
        
        stage('Build the code')
        {
            steps{
            sh 'mvn clean install package'
            }
        }
        
        stage('Copy war file from target folder to workspace')
        {
            steps{
                sh 'cp /var/lib/jenkins/workspace/CICDpipeline/target/addressbook.war .'
            }
        }
        
        stage('Build Image')
        {
            steps{
                sh 'docker build -t myappjenkins:$BUILD_NUMBER .'
            }
        }
        
        stage('Deploy the Image')
        {
            steps{
                sh 'docker run -d -P myappjenkins:$BUILD_NUMBER'
                sh 'docker ps'
            }
        }
        
    }
    
}
