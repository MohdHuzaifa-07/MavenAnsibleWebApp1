pipeline {
agent any

```
environment {
    LANG = 'en_US.UTF-8'
    LC_ALL = 'en_US.UTF-8'
}

tools {
    maven 'Maven'
}

stages {

    stage('Checkout') {
        steps {
            git branch: 'master', url: 'https://github.com/ShruthiBGowda/MavenAnsibleWebApp1-CICD.git'
        }
    }

    stage('Build') {
        steps {
            sh 'mvn clean package'
        }
    }

    stage('Archive') {
        steps {
            archiveArtifacts artifacts: 'target/*.war', fingerprint: true
        }
    }

    stage('Deploy') {
        steps {
            sh '''
            export ANSIBLE_HOST_KEY_CHECKING=False
            ansible-playbook -i ansible/hosts.ini ansible/playbook.yml
            '''
        }
    }

}
```

}

