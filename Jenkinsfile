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
  }

}

