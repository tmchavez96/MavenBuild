node('master') {

stage ('checkout code'){
	checkout scm
}
	
stage ('Build'){
	sh "mvn clean install"
}

stage ('Test Cases Execution'){
	sh "mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent install -Pcoverage-per-test"
}

stage ('Sonar Analysis'){
	//sh 'mvn sonar:sonar -Dsonar.host.url=http://localhost:80'
}

stage ('Archive Artifacts'){
	archiveArtifacts artifacts: 'target/*.war'
}
	
stage ('Deployment'){
	//sh 'cp target/*.war /opt/tomcat8/webapps'
}
	
stage('Notification'){
	slackSend color: 'good', message: 'Deployment Sucessful'
	emailext (
		subject: "Job Completed(yeeted)",
		body: "A great success!",
		to: "tmchavez96@gmail.com"
	)
}
	
}
