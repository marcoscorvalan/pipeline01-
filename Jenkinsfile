#!/usr/bin/env groovy
pipeline {

    agent any
      stages {

	stage('Checkout git repo and Get the Tag'){
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
    		  env.tags = sh(returnStdout: true, script: "git tag --sort=v:refname | tail -1")
    		  stringTags = env.tags
			  lisTags = stringTags.tokenize('-')
			  println('Show tokenize: ' + lisTags);
			  env.partition = lisTags.get(0);
			  env.product = lisTags.get(1);
			  env.silo = lisTags.get(2);
			  env.enva = lisTags.get(3);
			  println('Show partitions: ' + env.partitions);
			  println('Show product: ' + env.product);
			  println('Show silo: ' + env.silo);
			  println('Show env: ' + env.enva );

					}
    	   	   } 
    		}

    stage('Build Import Variable from List...') {
          agent { label 'master' }
              steps {
                script {
                     sh """
                    		tag=${env.tags}
                    		echo 'tag is: '\$tag
                    		partition=${env.partition}
                    		echo 'partition is: '\$partition
                		"""

                                }
                           }
                      }
		 }
    }
