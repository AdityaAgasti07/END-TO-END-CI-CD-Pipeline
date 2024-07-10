pipeline {
    agent {
        label 'slave2'
    }
    
    stages {
        stage('checkout') {
            steps {
                git 'https://github.com/devopsbyraham/jenkins-java-project.git'
            }
        }
        stage('build') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('code quality') {
            steps {
                sh '''
                mvn sonar:sonar \
                  -Dsonar.projectKey=new \
                  -Dsonar.host.url=http://15.236.204.150:9000 \
                  -Dsonar.login=4c2af25ea47794c3c8e9ccbb2e347c2e7b2dd7e2
                '''
            }
        }
        stage('artifact') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('deploy') {
            steps {
                deploy adapters:[
                    tomcat9(
                        credentialsId: '47267833-b417-45ab-a351-5014ab1b50d4',
                        path: '',
                        url: 'http://35.180.97.49:8080/'
                        )
                    ],
                    contextPath: 'netflix',
                    war: 'target/*.war'
            }
        }
    }
}
