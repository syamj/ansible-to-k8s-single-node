stage 'Checking connectivity'

node {
    deleteDir()
    checkout scm
    
    wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]) {
        ansiblePlaybook(
            playbook: 'ping.yml',
            inventory: 'hosts',
            credentialsId: 'ssh-ubuntu',
            colorized: true)
    }
}


stage "Deploy"

node {
    wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]) {
        ansiblePlaybook(
            playbook: 'create-cluster-playbook.yaml',
            inventory: 'hosts',
            credentialsId: '96b3fe82-e6a4-45eb-9e8d-0a512cba5a9c',
            colorized: true
            )
    }
}
