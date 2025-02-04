pipeline {
    agent {
        node {
            label 'slave'
        }
    }
    stages {
        stage('build') {
            steps {
                sh 'export PATH=$HOME/.nvm/versions/node/v20.18.2/bin:$PATH && npm install'
                sh 'export PATH=$HOME/.nvm/versions/node/v20.18.2/bin:$PATH && npm run build'
            }
        }
        stage('nexus') {
            steps {
                sh 'zip -r lms-v1.1.zip dist/*'
                sh 'pwd'
                sh 'curl -v -u admin:admin123 --upload-file lms-v1.1.zip http://18.144.90.12:8081/repository/lms/'
            }
        }
    }
}
