pipeline {
    agent {
        docker { image 'public.ecr.aws/docker/library/maven:3.9-sapmachine' }
        args '-u root'
    }
    stages {
        stage('Source'){
            steps {
                sh 'mvn --version'
                sh 'git --version'
                git branch: 'master', url: 'https://github.com/vikaskaushik3/run_pipeline_on_docker_agent.git'
            }
        }

        stage('Clean') {
            steps {
                dir("${env.WORKSPACE}/Ch04/04_03-docker-agent"){
                    sh 'mvn clean'
                }
            }
        }

        stage('Test'){
            steps{
                dir("${env.WORKSPACE}/Ch04/04_03-docker-agent"){
                    sh 'mvn test'
                }
            }
        }

        stage('Package'){
            steps{
                dir("${env.WORKSPACE}/Ch04/04_03-docker-agent"){
                    sh 'mvn package -DskipTests'
                }
            }
        }        
    }
}