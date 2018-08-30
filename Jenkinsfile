#!/usr/bin/groovy

@Library('github.com/piyush1594/fabric8-pipeline-library@nodejs')
def canaryVersion = "1.0.${env.BUILD_NUMBER}"
def utils = new io.fabric8.Utils()
def stashName = "buildpod.${env.JOB_NAME}.${env.BUILD_NUMBER}".replace('-', '_').replace('/', '_')
def envStage = utils.environmentNamespace('stage')
def envProd = utils.environmentNamespace('run')
def setupScript = null

fabric8UINode {
  if (utils.isCI()) {
    mavenCI{}
  } else if (utils.isCD()) {    
    container(name: 'ui', shell: '/bin/bash') {
      sh """
      env
      echo \$SHELL
      which node
      npm version
      node --version
      sleep infinity
      """
    }
  }
}
