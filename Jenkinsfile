pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // excute cmd with sh 
                sh 'rm -rf build'
                sh 'mkdir build'
                sh 'touch build/car.txt'
                // ">" replact entire contents in the file 
                // ">>" append
                sh 'echo "chassis" >> build/car.txt'
                sh 'echo "engine" >> build/car.txt'
                sh 'echo "body" >> build/car.txt'
            }
        }
        // automatically check if there's a car.txt
        stage('Test'){
            steps{
                // the file was created 
                sh 'test -f build/car.txt'
                sh 'grep "chassis" build/car.txt'
                
            }
        }
        stage('Publish'){
            steps{
                archiveArtifacts artifacts: 'build/'
            }
        }
    }
}
