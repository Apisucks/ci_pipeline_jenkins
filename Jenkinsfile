pipeline {
    agent any

    stages {
        // stage('Hello') {
        //     steps {
        //         echo 'Hello World from Repo'
        //         sh "ctag=`git tag --sort=-committerdate | head -1`; git checkout $ctag"
        //     }
        // }
            stage('Checkout') {
                steps {
                    // script {
                    //     // Fetch tags and branches
                    //     // def tags = sh(
                    //     //     script: "git ls-remote --tags origin | awk '{print \$2}' | grep 'refs/tags/' | sed 's@refs/tags/@@' | sort -V",
                    //     //     returnStdout: true
                    //     // ).trim().split('\n')
                    //     def tags = sh(
                    //         script: "git tag --sort=-committerdate | head -1",
                    //         returnStdout: true
                    //     ).trim().split('\n')
                    //     // (Optional) Filter tags for the specific branch if needed.
                    //     // Assuming a naming convention like `branch-name/v1.0.0`
                    //     def branch = 'main'
                    //     def filteredTags = tags.findAll { it.startsWith("${branch}/") }

                    //     // Get the latest tag (last entry after sorting)
                    //     def latestTag = filteredTags[-1] ?: tags[-1] // Fallback to any latest tag if branch filtering is empty.

                    //     echo "Latest tag for branch '${branch}': ${latestTag}"

                    //     // Checkout the latest tag
                    //     checkout([$class: 'GitSCM',
                    //         branches: [[name: "refs/tags/${latestTag}"]],
                    //         userRemoteConfigs: [[url: 'https://github.com/Apisucks/ci_pipeline_jenkins.git']]
                    //     ])
                    // }
                    sh "git rev-parse HEAD"
                    script {
                        def latestTag = sh(
                            script: "git tag --sort=-committerdate | head -1",
                            returnStdout: true
                        )

                        sh "git rev-parse -n 1 ${latestTag}"
                        sh "git show-ref ${latestTag}"

                        echo "${latestTag}"
                            // Checkout the latest tag
                        checkout([$class: 'GitSCM',
                            branches: [[name: "refs/tags/${latestTag}"]],
                            userRemoteConfigs: [[url: 'https://github.com/Apisucks/ci_pipeline_jenkins.git']]
                        ])
                    }
                    sh "git rev-parse HEAD"
                }
        }
        stage('Build') {
            steps {
                echo 'Build in progress from Repo'    
                sh "cat README.md"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploy in progress from Repo'    
            }
        }
    }
}