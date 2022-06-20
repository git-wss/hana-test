pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                 sh('/var/cx-server/mtar/mbt build -p=xsa')
            }
        }
    }
}
