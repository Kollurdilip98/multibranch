pipeline
{
    agent any
    
    stages()
    {
        stage('download')
        {
            steps()
            {
                git 'https://github.com/Kollurdilip98/Developer-Code.git'
            
            }
              }
        stage('build')
        {
            steps()
            {
                sh 'mvn package'
            }
        }
         stage('continous deploy')
        {
            steps()
            {
                
                deploy adapters: [tomcat9(credentialsId: 'none', path: '', url: 'http://54.209.96.100:8080')], contextPath: 'test', war: '**/*.war'
            
            }
        }  
         stage('continous testing')
        {
            steps()
            {
             git 'https://github.com/Kollurdilip98/Testing-Code.git'
             sh 'java -jar /var/lib/jenkins/workspace/Declarative@2/testing.jar'
            }   
        }
          stage('continous delivery')
        {
            
            steps()
            {
               deploy adapters: [tomcat9(credentialsId: 'none', path: '', url: 'http://54.196.249.132:8080')], contextPath: 'prod', war: '**/*.war'
              
            }   
        }
    }
}  
