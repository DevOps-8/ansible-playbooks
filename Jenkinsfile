#!/usr/bin/env groovy

def ansibleCredsId = "a490c6ab-bf59-4e2a-be13-a3ad8678344f"
def ansibleForks = 5
def ansibleForksInt = Integer.parseInt(ansibleForks)

node {
    deleteDir()

    try {
      stage ('Clone') {
        checkout scm
      }
      stage ('Bootstrap') {
        ansiColor('xterm') {
          ansiblePlaybook(
            inventory: '${WORKSPACE}/inventory',
            playbook: '${WORKSPACE}/bootstrap/playbook.yml',
            colorized: true,
            credentialsId: '${ansibleCredsId}',
            forks: '${ansibleForksInt}'
            )
        }
      }
    }
    catch (err) {
      currentBuild.result = "Failed"
      throw err
    }
}
