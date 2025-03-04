pipeline {
  agent any
  tools {
    jdk 'JAVA_HOME'
    maven 'M2_HOME'
  }
  
  stages {
    stage('GIT') {
      steps {
        git branch: 'anis', url: 'https://github.com/anisbm3/jenkins.git'
      }
    }
    stage('Compile Stage') {
      steps {
        sh 'mvn clean compile'
      }
    }
   /*stage('SonarQube Analysis') {
            steps {
                sh 'mvn sonar:sonar -Dsonar.token=sqa_2ce8c7b0b26806111384d5c23d29d396a3471b1c -Dmaven.test.skip=true';
            }
    }*/
/* stage('MVN Nexus'){
    		steps {
    			sh 'mvn deploy -Dmaven.test.skip=true'
    		}
	    }*/
stage('Docker Image Stage') {
    steps {
        sh """
            # Login to Docker
            docker login -u anisbm3 -p 25/01/2003
            
            # Tag the already built image with a new tag
            docker tag anisbm3/timesheet:1.0.0 anisbm3/timesheet:new-tag
            
            # Push the image with the new tag
            docker push anisbm3/timesheet:new-tag
        """
    }
}


                  
  }
}
