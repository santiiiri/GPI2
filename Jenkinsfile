pipeline {
    
    stages {
		stage('git') {
			steps { git url: 'https://github.com/santiiiri/GPI2.git' }
		}
		
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
				echo 'Arduino'
				dir('GPI2/arduino/Bare-Arduino-Project-master'){ 
					sh 'make -f Makefile-Linux.mk' 
				}
				echo 'Simple maven'
				dir('GPI2/simple') {
					sh 'mvn verify'
					sh 'mvn site'
				}
				echo 'Android'
				dir('GPI2/app android'){
					sh './gradlew tasks'
					sh './gradlew check'
				}
			}	
        }
    }
}

