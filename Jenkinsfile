pipeline {
agent {
label 'build-server'
}

stages {

stage ('Checkout') 
{
steps
    {
    
        checkout scm
        
    }
    
}
stage ('Build1') 
{
    steps
    {
        sh "cd /home/ubuntu/workspace/JnekinsPipelneDevOps"${Service_name}" ; mvn clean install " 
    }
}
    stage ('dockerbuild') 
{
    steps
    {
       sh "cd /home/ubuntu/workspace/JnekinsPipelneDevOps/${Service_name} ; sudo docker build -t ${Service_name} . " 
    }
}
     stage ('dockerimagepush ') 
{
    steps
    {
       sh "cd /home/ubuntu/workspace/JnekinsPipelneDevOps/ ${Service_name}; sudo  docker login -uankit1111 -pmiet@1234 "
        sh "cd /home/ubuntu/workspace/JnekinsPipelneDevOps/${Service_name} ; sudo docker tag account-service ankit1111/account-service  "
        sh "cd /home/ubuntu/workspace/JnekinsPipelneDevOps/ ${Service_name}; sudo docker push ankit1111/account-service   "
        
        
    }
}
    
    
stage ('k8sdeployment') 
    {
        steps {
            node (' Ansilbe') {
       sh " sudo ansible-playbook /root/dep.yml "
   
    }
}
}
}
    
    
}
