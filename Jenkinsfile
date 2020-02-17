node {
stage('Git-Checkout') {
   git 'https://github.com/amitvashisttech/mindtree-devops-30Jan2020.git'
  }
    stage('Maven-Clean') {
   sh label: '', script: 'mvn clean'
  }
    
 stage('Maven-Compile') {
   sh label: '', script: 'mvn compile'
  }
  
   stage('Maven-Test') {
   sh label: '', script: 'mvn test'
  }
  
   stage('Maven-Package') {
   sh label: '', script: 'mvn package'
   sh label: '', script: 'cp -rf target/*.war ../ansible/templates/apps/'
  }
  def project_path="/ansible/"
 dir(project_path) {
  stage('Ansible')
  {
  sh label: 'ansible', script: 'ansible-playbook -i inventory -u ubuntu --key /root/.ssh/coekey.pem coeplaybook.yaml'
  }
  }
}
