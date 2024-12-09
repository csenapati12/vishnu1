pipeline{
    agent any
    stages{
        stage("checkout"){
            steps{
                echo "Checkout"
                checkout changelog: false, poll: false, scm: scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/csenapati12/java-tomcat-maven-docker.git']])
            }
        }
        stage("build"){
            steps{
                echo "build"
            }
        }
        stage("Unit test"){
            steps{
                echo "Unit test"
            }
        }
    }
}
