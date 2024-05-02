import groovy.json.JsonOutput

pipeline {
    agent any

    stages {
        stage('git-clone') {
            steps {
                echo 'Cloning project'
            }
        }
        stage('exmample-acs-scan') {
            steps {
              script {
                    echo 'Example ACS Image Scan output'
                    scanOutputJson = '{  "result": {    "summary": {      "CRITICAL": 3,      "IMPORTANT": 33,      "LOW": 81,      "MODERATE": 107,      "TOTAL-COMPONENTS": 117,      "TOTAL-VULNERABILITIES": 224    },    "vulnerabilities": [      {        "cveId": "RHSA-2022:4797",        "cveSeverity": "IMPORTANT",        "cveInfo": "https://access.redhat.com/errata/RHSA-2022:4797",        "componentName": "aopalliance",        "componentVersion": "1.0-20.module+el8.3.0+6804+157bd82e.noarch",        "componentFixedVersion": "0:1.0-20.module+el8.6.0+13337+afcb49ec"      }]}';
                    prettyJSON = JsonOutput.prettyPrint(scanOutputJson)
                    echo "${prettyJSON}"
              }
            }
        }
        stage('example-acs-image-check') {
            steps {
              script {
                    echo 'Example ACS Image Check output'
                    scanOutputJson = '{"results":[{"metadata":{"id":"quay-bhlm4.apps.cluster-bhlm4.sandbox1077.opentlc.com/quayadmin/quarkus-app@sha256:66b6b795990a9eee32b5a0a6935d66a38d0317b1600c91e373326b08d3b58c3f","additionalInfo":{"name":"quay-bhlm4.apps.cluster-bhlm4.sandbox1077.opentlc.com/quayadmin/quarkus-app@sha256:66b6b795990a9eee32b5a0a6935d66a38d0317b1600c91e373326b08d3b58c3f","type":"image"}},"summary":{"CRITICAL":0,"HIGH":1,"LOW":1,"MEDIUM":0,"TOTAL":2},"violatedPolicies":[{"name":"Fixable Severity at least Important","severity":"HIGH","description":"Alert on deployments with fixable vulnerabilities with a Severity Rating at least Important","violation":["Fixable CVE-2022-4116 (CVSS 9.8) (severity Critical) found in component \'quarkus\' (version 2.11.3.final), resolved by version 2.13.5","Fixable CVE-2022-4147 (CVSS 7.5) (severity Important) found in component \'quarkus\' (version 2.11.3.final), resolved by version 2.13.5","Fixable CVE-2022-41881 (CVSS 7.5) (severity Important) found in component \'netty\' (version 4.1.78.final), resolved by version 4.1.86"],"remediation":"Use your package manager to update to a fixed version in future builds or speak with your security team to mitigate the vulnerabilities.","failingCheck":false},{"name":"Red Hat Package Manager in Image","severity":"LOW","description":"Alert on deployments with components of the Red Hat/Fedora/CentOS package management system.","violation":["Image includes component \'microdnf\' (version 3.8.0-2.el8.x86_64)","Image includes component \'rpm\' (version 4.14.3-19.el8_5.2.x86_64)"],"remediation":"Run `rpm -e --nodeps $(rpm -qa \'*rpm*\' \'*dnf*\' \'*libsolv*\' \'*hawkey*\' \'yum*\')` in the image build for production containers.","failingCheck":false}]}],"summary":{"CRITICAL":0,"HIGH":1,"LOW":1,"MEDIUM":0,"TOTAL":2 }}';
                    prettyJSON = JsonOutput.prettyPrint(scanOutputJson)
                    echo "${prettyJSON}"
              }
            }
        }
        
    }
}
