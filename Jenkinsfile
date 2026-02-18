pipeline{
    agent any

    stages{
        stage("Restore dependencies"){
            when{
                branch 'main'
            }
            steps{
                bat 'dotnet restore'
            }
            post{
                failure{
                    echo "Step failed"
                }
            }
        }

        stage("Build solution"){
            when{
                branch 'main'
            }
            steps{
                bat 'dotnet build --no-restore'
            }
        }

        stage("Run tests"){
            when{
                branch 'main'
            }
            steps{
                bat 'dotnet test --no-build --verbosity normal'
            }
        }
    }

    post{
        always{
            echo "Workflow completed successfully"
        }
    }
}