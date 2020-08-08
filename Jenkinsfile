pipeline {

    agent any
      stages {

	stage('Checkout git jobdsl2 N Get the Tag'){
		agent { label 'master' }
            steps{
	      		git credentialsId: 'jenkins-slave-docker', url: 'git@git.dlatv.net:mcorvalan/jobdsl2.git'
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
					  env.stringTags = tags
					  env.lisTags = stringTags.tokenize('-')
					  env.partitions = lisTags.get(0);
					  env.product = lisTags.get(1);
					  denv.silo = lisTags.get(2);
					  env.enva = lisTags.get(3);
				    println('Show partitions: ' + env.partitions)
				    println('Show product: ' + env.product)
				    println('Show silo: ' + denv.silo)
				    println('Show env: ' + env.enva)
					     }
    			  }
    		}
	stage('Build DockerFile...') {
          agent { label 'master' }
              steps {
                script {
                     sh "set brf = ${env.stringTags} && echo $brf"

                                }
                           }
                      }
		          }
    }
