#!/usr/bin/env groovy
pipeline {

    agent any
      stages {

	stage('Checkout git jobdsl2 N Get the Tag'){
		agent { label 'master' }
            steps{
	      		git credentialsId: 'jenkins', url: 'git@github.com:marcoscorvalan/pipeline01-.git'
	      	script {
        		tags = sh(script: "git tag --sort=v:refname | tail -1", returnStdout: true).trim()
					     }
					echo "I choose: '${tags}'"
				    }
	      	}

   stage ('Convert result to List and show it') {
		agent { label 'master' }
    		steps { echo "Convert result to List"
    		script {
    			tags = sh(returnStdout: true, script: "git tag --sort=v:refname | tail -1")
			  stringTags = tags
			  lisTags = stringTags.tokenize('-')
			  partitions = lisTags.get(0);
			  product = lisTags.get(1);
			  silo = lisTags.get(2);
			  enva = lisTags.get(3);
			  println('Show partitions: ' + partitions)
			    println('Show product: ' + product)
			    println('Show silo: ' + silo)
			    println('Show env: ' + enva)
					     }
    			  }
    		}
	stage('Build DockerFile...') {
          agent { label 'master' }
              steps {
                script {
                	env.tags = sh(returnStdout: true, script: "git tag --sort=v:refname | tail -1")
                     sh """
                    		brf=${env.tags}
                    		echo \$brf
                		"""

                                }
                           }
                      }
		          }
    }
