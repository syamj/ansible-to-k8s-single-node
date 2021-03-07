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
            credentialsId: 'ssh-ubuntu',
            colorized: true
            )
    }
}
