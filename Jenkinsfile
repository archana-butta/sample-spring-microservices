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
       sh "cd /home/ubuntu/workspace/JnekinsPipelneDevOps/account-service ; mvn clean install " 
    }
}
    stage ('dockerbuild') 
{
    steps
    {
       sh "cd /home/ubuntu/workspace/JnekinsPipelneDevOps/account-service ; sudo docker build -t account-service . " 
    }
}
     stage ('dockerimagepush ') 
{
    steps
    {
       sh "cd /home/ubuntu/workspace/JnekinsPipelneDevOps/account-service ; sudo  docker login -uankit1111 -pmiet@1234 "
        sh "cd /home/ubuntu/workspace/JnekinsPipelneDevOps/account-service ; sudo docker tag account-service ankit1111/account-service  "
        sh "cd /home/ubuntu/workspace/JnekinsPipelneDevOps/account-service ; sudo docker push ankit1111/account-service   "
        
        
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
