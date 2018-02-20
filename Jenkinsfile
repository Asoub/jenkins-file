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
			sh 'perl -i -pe\'s/\r$//;\' *.sh'
			sh 'ls'
			}
		}
	
	stage('build'){
		steps{
			sh 'ls'
			sh 'chmod u+rwx *.sh'
			input 'Container stopped 1'
			sh './_build.sh'
			input 'Container stopped 2'
			}
		}

	stage('unit-test'){
		steps{
			 sh '_unit-test.sh'
			}
		}

	stage('package'){
		steps{
			sh './_package.sh'
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