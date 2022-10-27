pipeline {
    agent { label 'JDK-11' }
    stages {
        stage('git clone') {
            steps {
                git url: "https://github.com/ksumankumar/js-e2e-express-server.git",
                    branch: "main"
            }
        }
        stage('build') {
            steps {
                sh """export PATH="/home/ubuntu/.nvm/versions/node/v16.18.0/bin:$PATH"
                      npm install
                      npm run build
                      npm test"""
            }
        }
        stage('archive artifact') {
            steps {
                archiveArtifacts artifacts: "src/**/*.js"
            }
        }

    }
}