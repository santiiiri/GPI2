pipeline {
   
    stages {
stage('git') {
sh 'git clone https://github.com/santiiiri/GPI2.git'
}

        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
echo 'Arduino'
dir('arduino/Bare-Arduino-Project-master'){
sh 'make -f Makefile-Linux.mk'
}
echo 'Simple maven'
dir('simple') {
sh 'mvn verify'
sh 'mvn site'
}
echo 'Android'
dir('app android'){
sh './gradlew tasks'
sh './gradlew check'
}
}
        }
    }
}

