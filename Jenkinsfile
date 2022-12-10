pipeline {
    agent {
        docker {image 'https://hub.docker.com/repository/docker/asuhail8/ecomm'}
    }
        parameters {
            choice(name: 'ENVIRONMENT', 
            choices : ['DEVELOPMENT', 'STAGING', 'PRODUCTION'],
            description : 'select the environment for deployement ?')

            password(name: 'API_KEY',
            defaultValue: '123ABC',
            description: 'Enter the API Key')

            text(name: 'CHANGE_LOG',
            defaultValue: 'This is the default changelog',
            description: 'This is the changelog')
        }

    stages{
        stage('Test'){
            steps{
                echo "Testing "
            }
        }
        stage('Deploy'){
            when{
                //only deploy to production env
                expression { params.ENVIRONMENT == 'PRODUCTION'}
            }
            steps{
            input message: 'Confirm deployement to production..', ok: 'Deploy'    
            echo "Deploying to ${params.ENVIRONMENT}"
        }
    }
    stage('Report'){
        steps{
            echo "report content contains : ${params.CHANGE_LOG}, ReportName : ${params.ENVIRONMENT}"
        }
    }    

    }
}