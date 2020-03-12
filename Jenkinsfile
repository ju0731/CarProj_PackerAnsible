pipeline {
  agent any
  stages {
    stage('Git clone') {
      steps {
        sh '''cd /var/lib/jenkins/workspace/
git clone "https://github.com/bsp-incubation/image.git"'''
      }
    }

    stage('Image Build') {
      steps {
        sh '''cd /var/lib
./packer build -var-file=/var/lib/jenkins/workspace/var.json /var/lib/jenkins/workspace/front_ami/AMI/packer/front_ami_build.json'''
      }
    }

    stage('Provisioning') {
      steps {
        sh '''cd /var/lib
./packer build -var-file=/var/lib/jenkins/workspace/var.json /var/lib/jenkins/workspace/front_ami/AMI/packer/front_ami_prov.json'''
      }
    }

  }
}