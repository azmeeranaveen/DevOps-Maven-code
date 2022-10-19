pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/Ersandeep977/DevOps-Maven-code.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'b6a3e172-533b-4d1a-9da0-10d82c1bc003', path: '', url: 'http://18.117.250.171:8080')], contextPath: 'test3', war: '**/*.war'
               }
        }
        stage('ContinuousTesting')
        {
            steps
            {
               git 'https://github.com/Ersandeep977/FunctionalTesting.git'
               sh 'java -jar /var/lib/jenkins/workspace/Pipeline-6/testing.jar'
            }
        }
       
    }    
}
