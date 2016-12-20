#!/usr/bin/env groovy

node ('base') {
	git 'https://github.com/eugeun/maven-scm.git'
	sh "${tool 'maven-3.3.9'}/bin/mvn -B clean verify"
	junit '**/target/surefire-reports/TEST-*.xml'
}
