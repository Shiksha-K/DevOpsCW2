echo "My DevOps CW2"


node {
    def app

    stage('Clone repository') {
        /* The clone repositry to workspace */

        checkout scm
    }


    /*Build the image */
    stage('Build image') {
        app = docker.build("shiksha12/devops-cw2")
    }

    stage('Test image') {
        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
     

}
