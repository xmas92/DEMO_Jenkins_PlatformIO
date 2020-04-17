pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''pio account logout || true
PLATFORMIO_AUTH_TOKEN=${BUILD_TOKEN} pio remote run -r
'''
      }
    }

    stage('Test') {
      steps {
        sh '''pio account logout || true
PLATFORMIO_AUTH_TOKEN=${TEST_TOKEN} pio remote test -e native -r
'''
        sh '''pio account logout || true
PLATFORMIO_AUTH_TOKEN=${TEST_TOKEN} pio remote test -r
'''
      }
    }

  }
  environment {
    BUILD_TOKEN = credentials('BUILD_TOKEN')
    TEST_TOKEN = credentials('TEST_TOKEN')
  }
}
