pipeline {
    agent any
      stages {

	stage('Checkout-git-jobdsl2-tec'){
		agent { label 'jenkins-slave-docker' }
            steps{
	      		git credentialsId: 'jenkins-slave-docker', url: 'git@git.dlatv.net:mcorvalan/jobdsl2.git'
	      	   	}
	      	}

    stage('Hello') {
    	agent { label 'jenkins-slave-docker' }
            steps { echo 'Hello World'
            script {
        		tags = sh(script: "git tag --sort=v:refname | tail -1", returnStdout: true).trim()
					}
					echo "I choose: '${tags}'"
              }
        }

	stage ('echo choose') {
		agent { label 'jenkins-slave-docker' }
    		steps { echo "I choose: '${tags}'"
    		script {
    				TAG = sh(returnStdout: true, script: "git tag --sort=v:refname | tail -1") 
					def sampleText = TAG
					println sampleText.tokenize('-')
    				}
    			}
    		}
	}

    }

