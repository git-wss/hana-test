pipeline {
    agent any
    environment {
        HANA_XSA_CREDS_PSW = credentials("xsa-user-pass")
    }
    stages {
        stage('Build') {
            steps {
                 sh('/var/cx-server/mtar/mbt build -p=xsa --mtar ${mtaName}.mtar')
            }
        }
        stage('Deploy') {
            steps {
                sh('/var/cx-server/bin/xs api https://hdx.gescher.wind-soft.de:30030 --skip-ssl-validation')
                sh('/var/cx-server/bin/xs login -u XSA_LINDE -p $HANA_XSA_CREDS_PSW -o WSS -s Basis')
                sh('/var/cx-server/bin/xs deploy -f ${WORKSPACE}/mta_archives/${mtaName}.mtar')
            }    
        }
    }
}
