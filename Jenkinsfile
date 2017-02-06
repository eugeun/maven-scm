#!/usr/bin/env groovy

node ('base') {
    stage ('Get Version') {
        checkout scm
		def v = version ()
		if (v) {
			echo "Building version ${v}"
		}
    }
}

def version() {
	def matcher = readFile('maven-scm-api/pom.xml') =~ '<version>(.+)</version>'
	matcher ? matcher[0][1] : null
}
