pipeline {
 agent any
 stages {
        stage('CreateVirtualEnv') {
            steps {
				sh '''
					bash -c "virtualenv entorno_virtual"
					bash -c "source entorno_virtual/bin/activate"
				'''

            }
        }
        stage('InstallRequirements') {
            steps {
            	sh '''
                	bash -c "pip install -r requirements.txt"
                '''
            }
        }   
        stage('TestApp') {
            steps {
            	sh '''
                	bash -c "cd src && pytest && cd .."
                '''
            }
        }  
        stage('RunApp') {
            steps {
            	sh '''
                	bash -c "python src/main.py &"
                '''
            }
        }         

  }
}

