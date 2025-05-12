pipeline {
    agent any

    environment {
        ANSIBLE_INVENTORY = 'inventory.ini'         // chemin relatif
        ANSIBLE_PLAYBOOK = 'deploy.yml'             // chemin relatif
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/med23009/IRT43.git'
            }
        }

        stage('Install Ansible') {
            steps {
                sh 'sudo apt-get update'
                sh 'sudo apt-get install -y ansible'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                ansiblePlaybook(
                    playbook: "${ANSIBLE_PLAYBOOK}",
                    inventory: "${ANSIBLE_INVENTORY}"
                )
            }
        }
    }
}

