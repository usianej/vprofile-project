pipeline {
    
	agent any

	tools {
        maven "MAVEN3"
        jdk "OracleJDK8"
    }

    environment {
        SNAP_REPO = "bimodal-snapshot"
        NEXUS_USER = "admin"
        NEXUS_PASS = "admin123"
        RELEASE_REPO = "bimodal-release"
        CENTRAL_REPO = "bimodal-maven-central"
        NEXUSIP = '54.157.239.106'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = "bimodal-maven-group"
        NEXUS_LOGIN = "nexuslogin"
        NEXUS_VERSION = "nexus3"
        NEXUS_PROTOCOL = "http"
        NEXUS_URL = "54.157.239.106:8081"
	    NEXUS_REPOGRP_ID    = "bimodal-maven-group"
        NEXUS_CREDENTIAL_ID = "nexuslogin"
        ARTVERSION = "${env.BUILD_ID}"
    }
	
    stages{
        
        stage('BUILD'){
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage('UNIT TEST'){
            steps {
                sh 'mvn -s settings.xml test'
            }
        }
        stage('Checkstyle Analysis'){
            steps {
                sh 'mvn -s settings.xml checkstyle:checkstyle'
            }
            post {
                success {
                    echo 'Checkstyle Analysis done successfully'
                }
            }
        }
    }
}