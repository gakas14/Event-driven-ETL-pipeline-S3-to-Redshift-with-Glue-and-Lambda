# Event-driven-ETL-pipeline-S3-to-Redshift-with-Glue-and-Lambda
https://medium.com/@abdoulkaled/event-driven-etl-pipeline-s3-to-redshift-with-glue-and-lambda-5b34e3f4971c


![ETL_job_s3_redshit](https://github.com/user-attachments/assets/3f9a73ae-45fc-4f5f-924b-5d0b19f359ff)


This project will build an automated data pipeline to move data from S3 to Redshift.

Once a file is in the S3 bucket, an S3 event notification triggers a lambda function that triggers the glue workflow. The workflow's started_trigger will first run a glue crawler to crawl the S3 bucket and create a table in the data catalog.

Once the crawler has finished successfully, a trigger(trigger_events_job) will run a glue job that converts the CSV file in the raw bucket into parquet and saves it in another S3 bucket (process bucket).

After creating the parquet file, a second trigger (trigger_events_job_redshift) will run a glue job to copy the data into a Redshift table.
