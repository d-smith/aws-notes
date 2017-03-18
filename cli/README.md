# Some Useful Commands

## Cloud Formation

List stacks

<pre>
aws cloudformation list-stacks --stack-status-filter CREATE_COMPLETE --region us-west-2
</pre>

List the resources associated with a stack

<pre>
aws cloudformation list-stack-resources --stack-name network --region us-west-2
</pre>

## S3

Copy a set of files to s3

<pre>
find . -name \*.yaml -exec aws s3 cp  {} s3://bucket/a-folder \;
</pre>
