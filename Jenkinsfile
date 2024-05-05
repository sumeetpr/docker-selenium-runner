pipeline{

    agent any

    stages{
        stage('Prepare selenium grid'){

            steps{
               bat "docker-compose -f grid.yaml up -d"
            }
        }
        stage('Run the Tests'){
             steps{
                 bat "docker-compose -f test-suites.yaml up"
            }
        }
    }
    post{
        always{
            bat "docker-compose -f grid.yaml down"
            bat "docker-compose -f test-suites.yaml down"
        }
    }
}