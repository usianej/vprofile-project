pipeline {
    
	agent any

	tools {
        maven "MAVEN3"
        jdk "OracleJDK8"
    }

    environment {
        SNAP_REPO = "bimodal-snapshot"
        RELEASE_REPO = "bimodal-release"
        CENTRAL_REPO = "bimodal-maven-central"
        NEXUSIP = '172.31.24.199'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = "bimodal-group"
        NEXUS_LOGIN = "nexuslogin"
        NEXUS_VERSION = "nexus3"
        NEXUS_PROTOCOL = "http"
        NEXUS_URL = "172.31.24.199:8081"
	    NEXUS_REPOGRP_ID    = "bimodal-maven-group"
        NEXUS_CREDENTIAL_ID = "nexuslogin"
        ARTVERSION = "${env.BUILD_ID}"
    }
	
    stages{
        
        stage('BUILD'){
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
        }
    }
}