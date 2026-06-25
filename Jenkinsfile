pipeline {
    agent any
    
    parameters {
        // Defines a drop-down menu for your Git Tags/Releases in the Jenkins UI
        gitParameter(
            name: 'RELEASE_TAG', 
            type: 'PT_TAG', 
            defaultValue: 'main', 
            description: 'Select the specific GitHub Release Tag to run'
        )
    }

    stages {
        stage('Checkout Source Code') {
            steps {
                script {
                    // Pulls code from your repo matching the selected release tag or branch
                    checkout([$class: 'GitSCM', 
                        branches: [[name: "refs/tags/${params.RELEASE_TAG}"]], 
                        userRemoteConfigs: [[
                            url: 'https://github.com/souravgit2021/demo-repo.git',
                            branches: 'main'
                        ]]
                    ])
                }
            }
        }
        stage('Execute Pipeline Tasks') {
            steps {
                echo "Successfully checking out and building from Release: ${params.RELEASE_TAG}"
                // Your build, test, or deployment commands go here
            }
        }

        stage("Greetings"){
            steps{
                 echo "Hellow From Release Version 3"
            }
        }
    }
}
