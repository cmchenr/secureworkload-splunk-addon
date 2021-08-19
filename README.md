## Packaging the App
This repo is a pre-liminary open-source release of a Splunk Add-on for assisting customers with effective parsing and indexing of Secure Workload Syslog alerts.  A pre-packaged tar.gz is provided in the root folder.  This can be downloaded and installed through the Splunk UI or by uzipping in the Splunk app folder. To package the app manually, you can clone the repository, zip the folder "TA_cisco-secureworkload-addon" and install as an app through the UI or by unzipping in into the Splunk Apps folder.

## App Readme
The Cisco Tetration Add-On for Splunk Enterprise enables appropriate parsing and indexing of Cisco Secure Workload (Tetration) Syslog alerts in Splunk.

This app provides visibility for end points and sensor collectors of the Tetration cluster, correlates with existing Splunk environment to derive insights and annotate inventory/flows in Tetration. Deep linking capability provided in the app redirects to the Tetration cluster to provide necessary flow information for the IP under inspection

1. Requirements for Add-on App
	Splunk version supported 8.0, and above
	Tetration 3.3 and Above
	Tetration user generated API_Key and Secret_key for collecting data from Tetration.

2. Installation of Add-on App
	Add-on app can be installed through UI using "Manage Apps" or extract tar.gz file directly into /opt/splunk/etc/apps/ folder.  The Add-on should be installed on the machine that is receiving the data input, such as a Heavy Forwarder.
	Restart Splunk
	Verify that the new "cisco:secureworkload:syslog" by navigating in Splunk to "Settings"->"Source Types" and search for "secureworkload"

3. Configuring the Input and Source TypeCreate a new data input for Secure Workload Syslog.  
    Secure Workload requires a dedicated input as the pre-processing done by the source type does not allow for auto-source type identification from a mixed stream of syslog inputs.  
    Create a new TCP or UDP input with a unique port for Secure Workload Syslog.  
    When configuring the input under "Set sourcetype" select "From List" then under "Source type" select "cisco:secureworkload:syslog".

4. Configuring the Secure Workload Syslog Connector
    Configure the Secure Workload Syslog connector to point to this port.  This will send generate a test message.  
    Navigate to search in Splunk and search for: "sourcetype=cisco:secureworkload:syslog".  If the add-on is working properly, you should see an indexed version of the test alert.