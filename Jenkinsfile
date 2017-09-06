pipeline {
 agent any
 stages {
        stage('test'){
          steps{
               sh '''
		bash -c "echo ${WORKSPACE}"
		'''
	  }
        }
        stage('Checkout-git'){
               steps{
		git poll: true, url: 'git@github.com:videocursoscloud/test-jenkins-1.git'
               }
        }
        stage('CreateVirtualEnv') {
            steps {
				sh '''
					bash -c "virtualenv entorno_virtual && source entorno_virtual/bin/activate"
				'''

            }
        }
        stage('InstallRequirements') {
            steps {
            	sh '''
            		bash -c "source ${WORKSPACE}/entorno_virtual/bin/activate; ${WORKSPACE}/entorno_virtual/bin/python ${WORKSPACE}/entorno_virutal/bin/pip ${WORKSPACE}/entorno_virtual/bin/pip install -r requirements.txt"
                '''
            }
        }   
        stage('TestApp') {
            steps {
            	sh '''
            		bash -c "source entorno_virtual/bin/activate; cd src && pytest && cd .."
                '''
            }
        }  
        stage('RunApp') {
            steps {
            	sh '''
            		bash -c "source entorno_virtual/bin/activate ; python src/main.py &"
                '''
            }
        } 
        stage('BuildDocker') {
            steps {
            	sh '''
            		docker build -t apptest:latest .
                '''
            }
        } 
    stage('PushDockerImage') {
            steps {
            	sh '''
            		docker tag apptest:latest mijack/apptest:latest
					docker push mijack/apptest:latest
					docker rmi apptest:latest
                '''
            }
        } 
  }
}

