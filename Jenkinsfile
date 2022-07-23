pipeline { 
  agent any

tools{
    nodejs 'Nodejs18'
  }
  
  stages { 
    stage('clone repository') {
      steps { 
        git 'https://github.com/RNyagah/gallery.git'
      }
    }
     stage('Build the project') {
      steps { 
        sh 'echo "here we will Build"'
      }
      
    }
    stage('Install Dependencies') {
      steps { 
        sh 'npm install'
      }
    }
    stage('Tests') {
      steps { 
        sh 'npm test'
      }
    }
    stage('Deploy Application') {
      steps {
            withCredentials([usernameColonPassword(credentialsId: 'Heroku', variable: 'HEROKU_CREDENTIALS' )]){
                    sh 'git push https://${HEROKU_CREDENTIALS}@git.heroku.com/beccaapp.git master'
              }
    }
  }
}
}