pipeline{
    agent any

    stages{
        stage("Restore dependencies"){
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
            steps{
                bat 'dotnet build --no-restore'
            }
        }

        stage("Run tests"){
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