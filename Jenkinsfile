#!/usr/bin/env groovy

stage ('scm') {
	node ('base') {
		checkout scm 
		stash 'maven_scm'
	}
}

stage ('build') {
	def splits = splitTests count(2)
	def branches=[:]

	for (int i=0; i < splits.size(); i++) {
		def index=i
		branches["split${i}"] = {
			node ('base') {
				deleteDir()
				unstash 'maven_scm'
				def exclusions = splits.get(index)
				writeFile file: 'exclusions.txt', text: exclusions.join("\n")
				sh "${tool 'maven-3.3.9'}/bin/mvn -B clean verify -Dmaven.test.failure.ingore"
				junit '**/target/surefire-reports/TEST-*.xml'
			}
		}
	}

	parallel branches
}

