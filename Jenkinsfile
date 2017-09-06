pipeline {
 agent any

 stages {
        stage('CreateVirtualEnv') {
            steps {
		sh '''
			#!/bin/bash
			virtualenv entorno_virtual
			source entorno_virtual/bin/activate
		'''
            }
        }
  }

}

