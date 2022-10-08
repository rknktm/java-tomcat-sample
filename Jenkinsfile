pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                sh 'mvn -f pom.xml clean package'
                }
            post {
                success {
                    echo "Now Archiving the Artifacts....."
                    archiveArtifacts artifacts: '**/*.war'
                        }
                }
        }
        stage('Deploy'){
        deploy adapters: [tomcat9(credentialsId: '23174692-6b02-4c00-be3c-25ab84439ac4', path: '', url: 'http://172.31.90.237:8080')], contextPath: null, war: '**/*.war'
        }
    }
}
