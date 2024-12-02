pipeline {
    agent any
    environment{
        name= 'chitransh'
    }
    parameters{
        string(name: 'person', defaultValue: 'chitransh jangid', description: 'who are you ?')
        booleanParam(name: 'MALE', defaultValue: true, description: "")
        choice(name: 'city', choices: ['jaipur', 'mumbai', 'goa'], description: 'Select a city')
    }
    stages {
        stage('run a command') {
            steps {
                sh '''
                date
                pwd
                cal 2025
                '''
            }
        }
        stage('environment variables') {
            environment{
                myusername= 'rsarswat'
            }
            steps {
                sh 'echo "${BUILD_ID}"'
                sh 'echo "${person}"'
                sh 'echo "${myusername}"'
            }
        }
        stage('deploy to test') {
            steps {
                echo 'deploying to testing server'
                sh 'echo "${myusername}"'
            }
        }
        stage('continue') {
            input{
                message "should we continue?"
                ok "yes we should"
            }
            steps {
                echo 'deploying to production server'
            }
        }
        stage('deploy to prod') {
            steps {
                echo 'deploying to production server'
            }
        }
    }
    post { 
        always { 
            echo 'always run the build either failed or success'
        }
        failure { 
            echo 'run when build is failed '
        }
        success { 
            echo 'run when build is success'
        }
    }
}
