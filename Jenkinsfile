node('jenkins-dockerInDocker') {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        sh "sleep 3600"
        app = docker.build("abokhan/test", "-f docker/Dockerfile docker")
    }

    stage('Test image') {
        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-abokhan') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
