pipeline {
	agent any
	
	stages {
		stage ('Kube Cleanup') {
			steps {
				echo "Cleaning up existing pod and service resources....."
				/usr/local/bin/kubectl delete -f /var/lib/jenkins/workspace/gitPull/deployment-nginx.yml 2>/dev/null || \
				/usr/local/bin/kubectl delete -f /var/lib/jenkins/workspace/gitPull/service-nginx.yml 2>/dev/null
			}
		}
		
		stage ('Kube Deploy') {
			steps {
				echo "Cleaning up existing pod and service resources....."
				/usr/local/bin/kubectl create -f /var/lib/jenkins/workspace/gitPull/deployment-nginx.yml && \
				/usr/local/bin/kubectl create -f /var/lib/jenkins/workspace/gitPull/service-nginx.yml
			}
		}
		
		stage ('Kube List Pods and Service') {
			steps {
				echo "Listing kubernetes pod and service resources....."
				/usr/local/bin/kubectl get all
			}
			
		}
	}
}
