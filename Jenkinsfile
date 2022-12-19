pipeline{
    agent {label 'OPENJDK-11'}

    environment{
        dockerhub=credentials('dockerhub')
    }

    stages{
        stage('pullig from svs'){
            steps{
                git url:'https://github.com/Sufiyan779/saleor-platform.git',
                branch: 'main'    
            }
        }
        stage('build image'){
            steps{
                sh 'docker image build -t saleor:1.0 .'    
            }
        }
        stage('pushing image into docker hub '){
            steps{
                sh 'docker tag saleor:1.0 sfn411/saleor:1.0'
                sh 'echo $dockerhub_PSW | docker login -u $dockerhub_USR --password-stdin'
                sh 'docker push sfn411/saleor:1.0'    
            }
        }
    }
}