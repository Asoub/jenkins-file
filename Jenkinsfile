pipeline{
	agent {
		node {
			label 'jenkins-slave-agent'
		}
	}

 stages {
	stage('proxy'){
		steps{
			//TMP_TEST
			sh 'pwd'
			sh 'cp -a /root/o2/. $(pwd)'
			sh 'perl -i -pe\'s/\r$//;\' *.sh' //dos2unix
			sh 'ls'
			}
		}
	
	stage('build'){
		steps{
			sh 'chmod u+rwx *.sh' //TMP_TEST
			sh './_build.sh'
			}
		}

	stage('unit-test'){
		steps{
			 sh './_unit-test.sh'
			 input 'Container stopped 2'
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