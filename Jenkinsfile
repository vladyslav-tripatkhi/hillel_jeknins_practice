pipeline {
    agent {
        label "docker"
    }

    environment {
        MY_ENV = "SOME_VALUE"
        OTHER_ENV = 123
        MY_DEFAULT_STRING="DEFAULT_STRING_FROM_ENV"
        SELECTED_AWS_REGION="${params.AWS_REGION}"
    }

    parameters {
        string(
            name: "my_string",
            defaultValue: "Hello, world, I am a variable!",
            description: "Just a string var"
        )

        choice(
            name: "AWS_REGION",
            choices: ["us-east-1", "us-west-1"],
            description: "AWS region name",
        )
    }

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
                echo "${params.my_string}, ${env.SELECTED_AWS_REGION}"
            }
        }
        
        stage("build") {
            steps {
                script{
                    docker.build("react-app:rest")
                }
            }
        }
    }
}