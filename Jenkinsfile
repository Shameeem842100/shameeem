pipeline {
    agent none

    stages {
        stage('build') {
            agent {
                label 'build-node'
            }

            steps {
                deleteDir()

                sh '''
                    git clone https://github.com/Shameeem842100/shameeem.git
                    ls -la
                '''

                stash name: 'webpage', includes: 'shameeem/**'
            }
        }

        stage('deploy') {
            agent {
                label 'deploy-node'
            }

            steps {
                deleteDir()

                unstash 'webpage'

                sh '''
                    sudo rm -rf /var/www/html/*
                    sudo cp -r shameeem/* /var/www/html/
                    ls -la /var/www/html/
                '''
            }
        }
    }
}
