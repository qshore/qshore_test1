node{
 stages{
	stage('maven isntall')
	{
		wget http://www-eu.apache.org/dist/maven/maven-3/3.5.2/binaries/apache-maven-3.5.2-bin.zip
		unzip apache-maven-3.5.2-bin.zip
		mv apache-maven-3.5.2/ /opt/maven
		ln -s /opt/maven/bin/mvn /usr/bin/mvn
		cd ~
		echo '#!/bin/bash
		MAVEN_HOME=/opt/maven
		PATH=$MAVEN_HOME/bin:$PATH
		export PATH MAVEN_HOME
		export CLASSPATH=.' | tee -a /etc/profile.d/maven.sh
		
		chmod +x /etc/profile.d/maven.sh
		source /etc/profile.d/maven.sh
		mvn -version
		}
	stage('install something wiht maven')
	{  
		checkout scm
		sh 'mvn clean install'
		}
		
		}
	}
