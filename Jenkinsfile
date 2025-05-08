LIBRARY_LIST_INBOUND=['CIFPolicySetsBindings', 'Common_Library', 'SOAPCIFMDMv11Library', 'SF_TO_CIF_ASYNC_MFP', 'REST_SF_TO_CIF_HUB']
pipeline{
    agent any
    stages{
        stage("checkout"){
            steps{
                echo "Checkout"
                checkout changelog: false, poll: false, scm: scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/csenapati12/java-tomcat-maven-docker.git']])
            }
        }
       stage('Deploying The Bar Files To ACE ')
 { 
 steps{
deployBar(LIBRARY_LIST_INBOUND, "${params.SERVER_CIF_INBOUND}");
 }
 }
 }
}
        stage("Unit test"){
            steps{
                echo "Unit test"
            }
        }
    }
}

def deployBar(list, server){
 for (int i = 0; i < list.size(); i++) {
 // Clean Before Deploying the other components 
 if (i == 0){
 bat(
 label: "Deploying ====> ${list[i]}",
 script: "\"${env.ACE_PATH}ace.cmd\"& \"${env.ACE_PATH}\\server\\bin\\mqsideploy.exe\" -i tcp://${USR_CREDS_USR}:${USR_CREDS_PSW}@${HOSTNAME}:${PORT} -a ${list[i]}.bar -m -e ${server}")
 }
 else {
 bat(
 label: "Deploying ====> ${list[i]}",
 script: "\"${env.ACE_PATH}ace.cmd\"& \"${env.ACE_PATH}\\server\\bin\\mqsideploy.exe\" -i tcp://${USR_CREDS_USR}:${USR_CREDS_PSW}@${HOSTNAME}:${PORT} -a ${list[i]}.bar -e ${server}")
 }
 }
}

