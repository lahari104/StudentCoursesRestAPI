// pipeline{
//     agent{
//         label 'node'
//     }
//     triggers{
//         pollSCM('* * * * *')
//     }
//     stages{
//         stage('clone'){
//             steps{
//                 git url: 'https://github.com/lahari104/StudentCoursesRestAPI.git',
//                     branch: 'master'
//             }
//         }
//         stage('build'){
//             steps{
//                 sh 'docker image build -t 647111907580.dkr.ecr.us-east-1.amazonaws.com/lahari:scr-3.0 .'
//                 sh 'docker push 647111907580.dkr.ecr.us-east-1.amazonaws.com/lahari:scr-3.0'
//             }
//         }
//     }
// }



pipeline{
    agent any
    stages{
        stage('clone'){
            steps{
                git url: 'https://github.com/lahari104/StudentCoursesRestAPI.git'
                branch: master
            }
        }
        stage('build'){
            steps{
                sh """
                      docker image build -t student:1.0 .
                      docker tag student:1.0 lahari23/studentcourserestapi:student-1.0
                      docker scan lahari23/studentcourserestapi:student-1.0
                      docker push lahari23/studentcourserestapi:student-1.0
                      docker image rm -rf student:1.0 lahari23/studentcourserestapi:student-1.0
                      docker image ls
                      """
            }
        }
        // stage('deploy'){
        //     steps{
        //         sh """
        //               Kubernets apply -f ./StudentCoursesRestAPI
        //               """
        //     }
        // }
    }
}