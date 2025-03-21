# Setting up replication<a name="replication-how-setup"></a>

**Note**  
Objects that existed before you set up replication aren't replicated automatically\. In other words, Amazon S3 doesn't replicate objects retroactively\. To replicate objects that were created before your replication configuration, use S3 Batch Replication\. Learn more about configuring Batch Replication at [Replicate existing objects](s3-batch-replication-batch.md)\.

To enable Same\-Region Replication \(SRR\) or Cross\-Region Replication \(CRR\), add a replication configuration to your source bucket\. The configuration tells Amazon S3 to replicate objects as specified\. In the replication configuration, you must provide the following:
+ **The destination buckets** – The bucket or buckets where you want Amazon S3 to replicate the objects\.
+ **The objects that you want to replicate** – You can replicate all of the objects in the source bucket or a subset\. You identify a subset by providing a [key name prefix](https://docs.aws.amazon.com/general/latest/gr/glos-chap.html#keyprefix), one or more object tags, or both in the configuration\.

   For example, if you configure a replication rule to replicate only objects with the key name prefix `Tax/`, Amazon S3 replicates objects with keys such as `Tax/doc1` or `Tax/doc2`\. But it doesn't replicate an object with the key `Legal/doc3`\. If you specify both a prefix and one or more tags, Amazon S3 replicates only objects that have the specific key prefix and tags\.

In addition to these minimum requirements, you can choose the following options: 
+ **Replica storage class** – By default, Amazon S3 stores object replicas using the same storage class as the source object\. You can specify a different storage class for the replicas\.
+ **Replica ownership** – Amazon S3 assumes that an object replica continues to be owned by the owner of the source object\. So when it replicates objects, it also replicates the corresponding object access control list \(ACL\)\. If the source and destination buckets are owned by different AWS accounts, you can configure replication to change the owner of a replica to the AWS account that owns the destination bucket\.

You can configure replication using the REST API, AWS SDKs, AWS Command Line Interface \(AWS CLI\), or the Amazon S3 console\. 

 Amazon S3 also provides API operations to support setting up replication rules\. For more information, see the following topics in the *Amazon Simple Storage Service API Reference*:
+  [PUT Bucket replication](https://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketPUTreplication.html) 
+  [GET Bucket replication](https://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketGETreplication.html) 
+  [DELETE Bucket replication](https://docs.aws.amazon.com/AmazonS3/latest/API/RESTBucketDELETEreplication.html) 

**Topics**
+ [Replication configuration](replication-add-config.md)
+ [Setting up permissions](setting-repl-config-perm-overview.md)
+ [Walkthroughs: Examples for configuring replication](replication-example-walkthroughs.md)