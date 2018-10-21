pipeline {
    agent any
    stages {
        stage('build') {
            steps {
		def app = docker.build("abokhan/test")
            }
        }
    }
}

