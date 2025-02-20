pipeline {
  agent any
  tools {
    jdk 'JAVA_HOME'
    maven 'M2_HOME'
  }
  
  stages {
    stage('GIT') {
      steps {
        git branch: 'projet', url: 'https://github.com/anisbm3/jenkins.git
      }
    }
    stage('Compile Stage') {
      steps {
        sh 'mvn clean compile'
      }
    }
   stage('SonarQube Analysis') {
            steps {
                sh 'mvn sonar:sonar -Dsonar.token=sqa_ee2388421e66eb10f3e4fa512f897cfba55c38ff -Dmaven.test.skip=true';
            }

    }
  }
}
