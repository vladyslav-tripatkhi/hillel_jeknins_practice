pipeline {
    agent any
    stages {
        stage("Checkout") {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/master']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/vladyslav-tripatkhi/react-redux-realworld-example-app.git'
                    ]]
                ])
            }
        }
        
        stage("First stage") {
            steps {
                echo "Hello! I'm a pipeline!"
                sh "sudo || echo 'no sudo'"   
            }
        }
        
        stage("second stage") {
            steps {
                echo "There is another stage!"
            }
        }
    }
}