# cbc_sourcetype_for_splunk
This add-on is meant to change sourcetype for VMware Carbon Black Cloud data.

## Features
This add-on was built to integrate the [Splunk Add-on for AWS](https://splunkbase.splunk.com/app/1876/) and [TA- VMware Carbon Black Cloud](https://splunkbase.splunk.com/app/5334), but it can be used independently from it.
In fact, at the time of development, the data was in an AWS S3 bucket. 

* Provides a dedicated sourcetype named `vmware:cbc:s3:events`,`vmware:cbc:s3:alerts`,`vmware:cbc:s3:watchlist:hits`
* The sourcetype matches the related field from logs before indexing the full event

## Getting Started

### Installation
Please refer to the [Splunk Documentation](https://docs.splunk.com/Documentation/SplunkCloud/latest/Admin/PrivateApps#Install_a_private_app_on_Classic_Experience) for guidance on installing the Add-On in your environment.


### Usage with Splunk Add-on for AWS
As mentioned in [official docs](https://docs.splunk.com/Documentation/AddOns/released/AWS/ConfigureInputs):
* Login into your Splunk instance and browse to the _Splunk Add-on for AWS / Inputs_
* If you haven't configured an AWS Account yet, browse to _Configuration / Account_, set one and then go back to _Inputs_
* Create a new Input by selecting on _Custom Data Type / Generic S3_
* Fill in requested data such as **Name**, **AWS Account**, **S3 bucket**, **index**, **Polling Interval**, etc
* Set **Source Type = vmware:cbc:s3:events** , **Source Type = vmware:cbc:s3:alerts** and **Source Type = vmware:cbc:s3:watchlist:hits**
* Add the input and enable it

You should now see data being ingested in the specified index.

## Troubleshooting
* Check ingestion of data in given index
`index=carbon_black sourcetype="vmware:cbc:s3:events"`
`index=carbon_black sourcetype="vmware:cbc:s3:alerts"`
`index=carbon_black sourcetype="vmware:cbc:s3:watchlist:hits"`

* Check for S3 logs
`index=_internal sourcetype="vmware:cbc:s3:events"`
`index=_internal sourcetype="vmware:cbc:s3:alerts"`
`index=_internal sourcetype="vmware:cbc:s3:watchlist:hits"`

## References
* [Configure AWS inputs](https://docs.splunk.com/Documentation/AddOns/released/AWS/ConfigureInputs)
* [Troubleshooting S3 issues](https://docs.splunk.com/Documentation/AddOns/released/AWS/Troubleshooting#S3_issues)
* [Ingest_eval usages](https://conf.splunk.com/files/2020/slides/PLA1154C.pdf)
* [Ingest_eval](https://docs.splunk.com/Documentation/Splunk/latest/Data/IngestEval)
* [Carbon Black Developer](https://developer.carbonblack.com/reference/carbon-black-cloud/integrations/splunk/installation-and-configuration/)

## License
This project is licensed under [Splunk Pre-Release Software License Agreement](LICENSE.md)