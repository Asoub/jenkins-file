pipeline{
	agent {
		node {
			label 'jenkins-slave-agent'
		}
	}

 stages {
	stage('proxy'){
		steps{
			//A tester
			//hostname = container id
			// sh 'docker cp /home/o $(hostname):$(pwd)'
			sh 'pwd'
			sh 'cp -a /root/o2/. $(pwd)'
			sh 'perl -i -pe\'s/\r$//;\' build.sh'
			}
		}
	
	stage('build'){
		steps{
			chmod u+rwx build.sh
			sh './build.sh'
			}
		}

	stage('unit-test'){
		steps{
			sh 'yarn test'
			}
		}

	stage('package'){
		steps{
			echo 'no package yet'
			//sh './package.sh'
			}
		}

	stage('func-test'){
		steps{
			echo 'no func-test yet'
			}
		}

	stage('Deliver') {
		steps {
			input 'Finished using the container ? (Click "Proceed" to continue)'
			}
		}
	}
}