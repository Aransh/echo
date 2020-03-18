pipeline {
    agent any

    triggers {
        git(
            triggerOnPush: true,
            triggerOnMergeRequest: true,
            branchFilterType: 'All',
            addVoteOnMergeRequest: true)
    }
    // options {
    //   gitLabConnection('gitlab')
    // }
    stages {
        stage('build') {
            steps {
                sh "echo test"
                // configFileProvider([configFile(fileId: 'artifactory', variable: 'MAVEN_SETTINGS_XML')]) {
                //     sh "mvn -s $MAVEN_SETTINGS_XML verify"
                // }
            }
        }
        // stage('test') {
        //     steps {
        //         script {
        //             MESSAGE=sh(script: "/bin/bash -c 'git log -1 --oneline | cut -f2'", returnStdout: true)
        //             withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'artifactory', usernameVariable: 'USER', passwordVariable: 'PASS']]) {

        //                 LATEST_TEST=sh(script: "/bin/bash -c 'curl -s -u $USER:$PASS http://artifactory:8081/artifactory/libs-snapshot-local/com/lidar/simulator/99-SNAPSHOT/maven-metadata.xml | grep value | head -n1'", returnStdout: true).trim()
        //                 LATEST_TEST=LATEST_TEST.substring(7, LATEST_TEST.indexOf("</value>"));
        //                 if ("$BRANCH_NAME" =~ /^(release)/){
        //                     MAJOR_VERSION=sh(script: "/bin/bash -c 'echo \$BRANCH_NAME | rev | cut -d / -f1 | rev'", returnStdout: true).trim() //x.y
        //                     LATEST_TELEMETRY=sh(script: "/bin/bash -c 'curl -s -u $USER:$PASS http://artifactory:8081/artifactory/libs-release-local/com/lidar/telemetry/maven-metadata.xml | grep version | grep -F ${MAJOR_VERSION}. | tail -n 1'", returnStdout: true).trim()
        //                     LATEST_TELEMETRY=LATEST_TELEMETRY.substring(9, LATEST_TELEMETRY.indexOf("</version>"));
        //                     sh "curl -s -u $USER:$PASS -o telemetry.jar 'http://artifactory:8081/artifactory/libs-release-local/com/lidar/telemetry/${LATEST_TELEMETRY}/telemetry-${LATEST_TELEMETRY}.jar'"
        //                 }
        //                 else{ 
        //                     LATEST_TELEMETRY=sh(script: "/bin/bash -c 'curl -s -u $USER:$PASS http://artifactory:8081/artifactory/libs-snapshot-local/com/lidar/telemetry/99-SNAPSHOT/maven-metadata.xml | grep value | head -n1'", returnStdout: true).trim()
        //                     LATEST_TELEMETRY=LATEST_TELEMETRY.substring(7, LATEST_TELEMETRY.indexOf("</value>"));
        //                     sh "curl -s -u $USER:$PASS -o telemetry.jar 'http://artifactory:8081/artifactory/libs-snapshot-local/com/lidar/telemetry/99-SNAPSHOT/telemetry-${LATEST_TELEMETRY}.jar'"
        //                 }

        //                 sh "curl -s -u $USER:$PASS -o test.jar 'http://artifactory:8081/artifactory/libs-snapshot-local/com/lidar/simulator/99-SNAPSHOT/simulator-${LATEST_TEST}.jar'"
        //             }
        //             if ("$BRANCH_NAME" =~ /^(master$|release)/ || ("$BRANCH_NAME" =~ /^(feature)/ && MESSAGE.contains("#e2e"))) {
        //                 // e2e testing
        //                 sh "mv tests-full.txt tests.txt"
        //             }
        //             else {
        //                 // sanity testing
        //                 sh "mv tests-sanity.txt tests.txt"
        //             } 
        //             sh "java -cp test.jar:telemetry.jar:target/analytics-99-SNAPSHOT.jar com.lidar.simulation.Simulator"
        //         }
        //     }
        // }
        // stage('publish') {
        //     when { 
        //         expression { BRANCH_NAME =~ /^(master$|release)/ }
        //     }
        //     steps {
        //         script{
        //             configFileProvider([configFile(fileId: 'artifactory', variable: 'MAVEN_SETTINGS_XML')]) {
        //                 if ("$BRANCH_NAME" == "master") {
        //                         sh "mvn -s $MAVEN_SETTINGS_XML deploy"
        //                 }
        //                 else {
        //                     MAJOR_VERSION=sh(script: "/bin/bash -c 'echo \$BRANCH_NAME | rev | cut -d / -f1 | rev'", returnStdout: true).trim() //x.y
        //                     MINOR_VERSION = sh(script: "/bin/bash -c 'git describe --tags | rev | cut -d . -f1 | rev | cut -d - -f1'", returnStdout: true) //z
        //                     if (MINOR_VERSION.isNumber()){
        //                         MINOR_VERSION = MINOR_VERSION.toInteger()+1
        //                     }
        //                     else {
        //                         MINOR_VERSION = 0
        //                     }
        //                     NEW_VERSION = "$MAJOR_VERSION"+"."+"$MINOR_VERSION"
        //                     sh 'git config --global user.email "aranshavit@gmail.com"'
        //                     sh 'git config --global user.name "Aransh"'
        //                     sh "git checkout $BRANCH_NAME"
        //                     sh 'git pull'
        //                     sh "git tag -a $NEW_VERSION -m $NEW_VERSION"
        //                     sh 'git push --follow-tags'
        //                     sh "mvn versions:set -DnewVersion=$NEW_VERSION"
        //                     sh "mvn -s $MAVEN_SETTINGS_XML deploy"
        //                 }
        //             }
        //         }
        //     }
        // }
    }
    // post { 
    //     always { 
    //         script{
    //             sh 'rm -rf * .git'
    //         }
    //     }
    //     failure {
    //         updateGitlabCommitStatus name: 'test', state: 'failed'
    //     }
    //     success {
    //         updateGitlabCommitStatus name: 'test', state: 'success'
    //     }
    // }
}