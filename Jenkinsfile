pipeline {
    agent any 
    stages {
      stage('descargar repositorio') {
        steps {
            git branch: 'main', url: 'https://github.com/HaroldDuvanPinillaSalinas/taller-devops'
            sh """
                docker build -t django .
            """
        }
      }
      stage('linter') {
        steps {
            sh """
               pwd
               pylint rp-portfolio
            """
        }
      }
      stage('ejecutar') {
        steps {
            sh """
                docker rm -f django
                docker run --rm -d --name django -p 8000:8000 django  
            """
        }
      }
    }
}

