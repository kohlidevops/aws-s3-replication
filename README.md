# aws-s3-replication

**To Configure Replication rule and check how its working between and Origin and Replica bucke**t

**Create one s3 bucket in origin region**

To create a s3 bucket with enable Versioning in Origin region (ap-south-1). In my case, I'm choosing ap-south-1

<img width="778" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/d94704c8-0628-47bf-9814-8400b3a01616">

**Create one s3 bucket in replica (destination) region**

To create a s3 bucket with enable Versioning in Origin region (us-east-1). In my case, I'm choosing us-east-1. So I have 2 buckets, one for origin and another one for replication.

<img width="809" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/1512eaa0-abd9-4db5-8f9b-851ff5c92294">

**To upload one file to origin s3 bucket**

<img width="461" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/00e3e937-98cb-4805-a48f-849b17bbb0d8">

**Create new Replication rule in Origin S3 bucket**

<img width="819" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/0951b5f4-c31a-4d94-bb5a-b758b3a71a8a">

<img width="778" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/db59bc74-c4ca-496c-8dc2-173fd3428de6">

When you save this replication rule, it will ask you to replicate existing object or newer uploads.

<img width="534" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/1c5f7157-5e12-481d-b570-c41b5872a779">

I'm go with newer uploads only means "No, do not replicate existing objects"

Now, Replication rule is ready

<img width="868" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/6c09c970-cba7-43ae-96a2-f7a8f710634f">

**I just uploaded new object in Origin S3 bucket that is s3-latchu-origin**

<img width="701" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/09b21942-6880-47b2-8170-5b6bb161de7e">

**I can able to see my Version ID for Origin bucket. Because we have been enabled Version for Origin while creating bucket.**

<img width="833" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/442de91e-debe-43f4-93cf-6af591d1cf6d">

Successfully replication has been completed to destination bucket that is s3-latchu-replica

<img width="796" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/854cd12e-37dc-43e0-ae1f-48bb89b341d7">

**I can able to see Version ID for object which has been replicated from origin bucket. Because we have enabled Version while creating replica bucket.**

**Hey, Version ID should be same for origin and replica bucket object. You can notice.**

<img width="889" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/fc794a62-91f2-499f-a0b8-738d61f489b7">

**Now, Im going to upload same object (beach.jpg) as versioning to origin bucket that is s3-latchu-origin.**

<img width="542" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/b1a92f53-cc26-4741-bde3-fbd894e852f0">

**I can see the new version of beach.jpg object.**

<img width="845" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/78d0daed-b82a-41f3-9934-a6e8d45a0bf7">

**Same Version ID has been applied to replica s3 bucket.**

<img width="827" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/3087ecab-f09a-42ca-a69c-944f5ca520c5">

I will edit the replication rule in my s3-latchu-origin bucket, enable **"Delete Marker Replication"** in Additional replicatio settings.

<img width="647" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/e0f3e08d-eff0-4834-aedf-643a2f147079">

What will happen, If I will delete the particular object (coffee.jpg) from s3-latchu-origin bucket after enable "Delete Marker Replication" in Replication rule.

<img width="770" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/e5e60c92-d3f9-4c34-9d13-ef9799d3a3bf">

The particular object (coffee.jpg) has been deleted from s3-latchu-replica bucket.

<img width="660" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/6c4fff5b-62ad-465f-abab-1b6f8d661977">

But If i show Versions in s3-latchu-replica bucket, You can see the **"Delete Marker"** has been **replicated to s3-latchu-replica bucket from s3-latchu-origin** bucket.

<img width="700" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/4860839e-aa66-450a-835e-573a2cfc0ab1">

If I'm going to delete the specific Version of object from s3-latchu-origin bucket,

<img width="839" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/084d3356-16d6-45e8-a38f-b026bb8d797a">

**The particular Version of object has not been deleted from s3-latchu-replica bucket. Because only "Delete Marker" are Replicated, Not delete.**

<img width="867" alt="image" src="https://github.com/kohlidevops/aws-s3-replication/assets/100069489/d34ece70-1206-40b9-9c3e-b5331ec94ca9">

That's it.

