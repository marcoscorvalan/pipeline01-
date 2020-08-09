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
    			def tags = sh(returnStdout: true, script: "git tag --sort=v:refname | tail -1")
    			stringTags = tags
			  lisTags = stringTags.tokenize('-')
			  println('Show tokenize: ' + lisTags);
			  env.partition = lisTags.get(0)
			  println('Show = partition: ' + env.partition );
					}
    	   	   } 
    		}

    stage('Build Import Variable from List...') {
          agent { label 'master' }
              steps {
                script {
                     sh """
                    		tag_name=${tags}
                    		echo \$tag_name
                    		partition_name=${env.partition}
                    		echo \$partition_name
                		"""

                                }
                           }
                      }
		 }
    }
