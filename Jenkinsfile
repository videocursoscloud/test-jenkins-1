pipeline {
 agent any

 stages {
        stage('CreateVirtualEnv') {
            steps {
		sh '''
			bash virtualenv entorno_virtual
			bash source entorno_virtual/bin/activate
		'''
            }
        }
  }

}

