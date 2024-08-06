pipeline{
    agent any
    tools{
        maven 'local_maven'
    }
    stages{
        stage('Build')
          sh 'mvn clean package'
    }
    post {
        success{
            echo "Archiving the artifacts"
            ArchiveArtifact artifacts: '**/target/*.war'
        }
    }
    stage('Deploy to tomcat')
    {
steps{
    deploy adapters: [tomcat9(credentialsId: 'c658ebb8-03ab-48fa-9357-e44739de94bf', path: '', url: 'http://ec2-3-85-37-186.compute-1.amazonaws.com:8080/')], contextPath: null, war: '**/*.war'
}
    }
}
