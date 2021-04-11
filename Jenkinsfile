pipeline {
  agent any
  stages {
    stage('') {
      steps {
        dockerNode(image: 'maven:3-alpine') {
          git(url: 'https://github.com/Tamilvananv/HCL', branch: 'Main')
        }

      }
    }

  }
}