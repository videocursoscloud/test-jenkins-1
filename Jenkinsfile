pipeline {
 agent any

 stages {
        stage('CreateVirtualEnv') {
            steps {
		sh '''
			virtualenv entorno_virtual
			source entorno_virtual/bin/activate
		'''
            }
        }
  }

}

