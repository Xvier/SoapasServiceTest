#!groovy

node('soapuislave') {

	    currentBuild.result = "SUCCESS"

	try{
		stage 'Checkout'
		def soapHome = '/opt/soapui/SoapUI-5.2.1/bin'
		checkout scm
		echo "Checked out the project"

		stage 'Start Soap Test'
		sh "${soapHome}/testrunner.sh -J -j -A BLZ-soapui-project.xml"

		stage 'Start Bol.com Rest Test'
		sh "${soapHome}/testrunner.sh -J -j -A Bol-soapui-project.xml"

		stage 'Archive Results'
		step([$class: 'JUnitResultArchiver', testResults: 'TEST-*.xml'])

	}
	   catch (InterruptedException x) {
      currentBuild.result = "ABORTED"
  } catch (e) {
      currentBuild.result = "FAILED"
      throw e
  }
}