pipeline{
    agent{
        label 'node'
    }
    triggers{
        pollSCM('* * * * *')
    }
    stages{
        stage('clone'){
            steps{
                git url: 'https://github.com/lahari104/StudentCoursesRestAPI.git',
                    branch: 'master'
            }
        }
        stage('build'){
            steps{
                sh 'docker image build -t 647111907580.dkr.ecr.us-east-1.amazonaws.com/lahari:scr-3.0'
                sh 'docker push 647111907580.dkr.ecr.us-east-1.amazonaws.com/lahari:scr-3.0'
            }
        }
    }
}