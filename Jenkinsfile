pipeline
{
    agent any
    stages
    {
        stage('ContinousDown')
        {
        steps
        {
            git 'https://github.com/intelliqittrainings/maven.git'
        }
        }
        stage('Continousbuild')
        {
        steps
        {
            sh 'mvn package'
        }
        }
        stage('ContinousDeployment')
        {
        steps
        {
            deploy adapters: [tomcat9(credentialsId: 'db900297-60e6-45be-b9f5-2ad129935706', path: '', url: 'http://13.233.113.187:8080')], contextPath: 'mytestapp', war: '**/*.war'
        }
        }
        stage('Continoustesting')
        {
        steps
        {
            git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
            sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline/testing.jar'
        }
        }
        stage('ContinousDelivery')
        {
        steps
        {
            deploy adapters: [tomcat9(credentialsId: 'db900297-60e6-45be-b9f5-2ad129935706', path: '', url: 'http://3.110.32.107:8080')], contextPath: 'myprodapp', war: '**/*.war'
        }
        }
    }
        
}
