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
    			env.tags = sh(returnStdout: true, script: "git tag --sort=v:refname | tail -1")
			  env.stringTags = env.tags
			  env.lisTags = env.stringTags.tokenize('-')
			  println('Show tokenize: ' + env.lisTags);
			  println(env.lisTags[0]);
			
			  
			  
			  
					     }
    			  }
    		}

		          }
    }
