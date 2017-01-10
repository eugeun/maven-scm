#!/usr/bin/env groovy

node ('base') {
  stage ('scm') {
  	checkout scm
  }
  
  stage ('compile') {
  	sh "${tool 'maven-3.3.9'}/bin/mvn -B clean compile -U"
  }
  
  stage ('package') {
  	sh "${tool 'maven-3.3.9'}/bin/mvn -B package"
  }

  stage ('update-version') {
    sh "${tool 'maven-3.3.9'}/bin/mvn -B release:update-versions"
  }
}
