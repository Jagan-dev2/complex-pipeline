pipeline{
    agent any
    stages{
        stage ('Build')
        {
            steps
            {
            echo "Build stage"
            }
        }
        stage('Deploy to Prod')
        {
            options{
            timeout(time : 60,unit:"SECONDS")
            }
            input {
                message "Approval for prod deployment"
                ok "Yes,Approved"
                submitter "Mohan"
                submitterParameter "Whoapproved"
                parameters{
                    string(
                        name : 'USR_NAME'
                        defaultValue : 'Prathi'
                        description : 'Enter your name'
                    )
                    string(
                        name : 'CHG_Tocket'
                        defaultValue : 'CHG123'
                        description : 'CR number'
                    )
                    booleanParam(
                        name : "SRE_Approved"
                        defaultValue : true
                        description : "Is approval taken from concern person"
                    )
                    choice(
                        name : "Release"
                        choices: "Release\nhotfix"
                        description : "Type of release,main or hotfix?"
                    )
                    text(
                        name : "Notes"
                        defaultValue : "Release to prodcution"
                        description : "Release notes"
                    )
                    credentials(
                        name : "my creds"
                        description: "MyCredentials"
                        required : true
                    )
                }
            }

            steps {
                echo "Deploying to production"
                echo "Welcome ${USR_NAME}"
                echo "status of approval ${SRE_Approved}"
                echo "This is a ${Release} release"
                echo "Approved by this person ${Whoapproved}"
            }
        }
    }
}
