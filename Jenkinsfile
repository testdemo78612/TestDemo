pipeline {

 

    agent any

 

    parameters {

 

        string(name: 'Branch', defaultValue: 'main', description: 'Branch to checkout')

 

        choice(name: 'BuildType', choices: ['debug', 'release', 'test'], description: 'Build types')

 

    }

 

    stages {

        stage('Git checkout') {

 

        steps {

 

             script {

 

                    def Branch = params.Branch

 

                    git([credentialsId: 'testDemoCred', url: 'https://github.com/testdemo78612/TestDemo.git', branch : Branch])

 

             }

 

            }

 

        }

 

        stage('build') {

 

            steps {

 

                echo "Branch value: ${params.Branch}"

 

                echo "BuildType value: ${params.BuildType}"

 

                script {

 

                    // Set JAVA_HOME environment variable

 

                    withEnv(["JAVA_HOME=/home/1036640@quest-global.com/android-studio-2022.2.1.20-linux/android-studio/jbr", "ANDROID_HOME =/home/1036640@quest-global.com/Android/Sdk"]) {

 

                        // Your pipeline steps go here

 

                        // The JAVA_HOME variable will be available within this block

 

                        def Branch = params.Branch

 

                        def BuildType = params.BuildType

 

                        if (BuildType == "debug") {

 

                            sh "./gradlew assembleDebug"

 

                        } else if (BuildType == "release") {

 

                            sh "./gradlew assembleRelease"

 

                        } else {

 

                            sh "./gradlew test"

 

                        }

 

                    }

 

                }

 

            }

 

        }

 

        stage('Archive Artifacts') {

 

            steps {

 

                // Archive the artifacts

 

                archiveArtifacts '**/*.apk'

 

            }

 

        }

 

    }

 

}
