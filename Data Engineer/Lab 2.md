# Perform Foundational Data, ML, and AI Tasks in Google Cloud: Challenge Lab

## Task 1: Run a simple Dataflow job
- In the Cloud Console, click on **Navigation Menu > BigQuery**.
- Select your project in the left pane.
- Click `CREATE DATASET`.
- Enter `lab` in the Dataset ID, then click **Create** dataset.
- Select the new dataset lab and click Create Table.
- In the Create table dialog, select **Google Cloud Storage** from the dropdown in the Source section.
- Copy `gs://cloud-training/gsp323/lab.csv` to **Select file from GCS bucket**.
- Enter `customers` to “Table name” in the Destination section
- Enable **Edit as text** and copy the following to the textarea in the Schema section.
```
    [
        {"type":"STRING","name":"guid"},
        {"type":"BOOLEAN","name":"isActive"},
        {"type":"STRING","name":"firstname"},
        {"type":"STRING","name":"surname"},
        {"type":"STRING","name":"company"},
        {"type":"STRING","name":"email"},
        {"type":"STRING","name":"phone"},
        {"type":"STRING","name":"address"},
        {"type":"STRING","name":"about"},
        {"type":"TIMESTAMP","name":"registered"},
        {"type":"FLOAT","name":"latitude"},
        {"type":"FLOAT","name":"longitude"}
    ]
```
- Click **Create table**.
- In the Cloud Console, click on **Navigation Menu > Storage**.
- Click **CREATE BUCKET**.
- Copy your **GCP Project ID** to Name your bucket.
- Click **CREATE**.
- Click **Check my progress** to verify the objective
- In the Cloud Console, click on **Navigation Menu > Dataflow**.
- Click **CREATE JOB FROM TEMPLATE**.
- In Create job from template, give an arbitrary job name.
- From the dropdown under Dataflow template, select **Text Files on Cloud Storage Pub/Sub under “Process Data in Bulk (batch)”**. 
> :warning: **(DO NOT select the item under “Process Data Continuously (stream)”).**

- Under the Required parameters, enter the following values:

Field |	Value
- | - 
JavaScript UDF path in Cloud Storage |	`gs://cloud-training/gsp323/lab.js`
JSON path | `gs://cloud-training/gsp323/lab.schema`
JavaScript UDF name | `transform`
BigQuery output table |	`YOUR_PROJECT:lab.customers`
Cloud Storage input path |	`gs://cloud-training/gsp323/lab.csv`
Temporary BigQuery directory |	`gs://YOUR_PROJECT/bigquery_temp`
Temporary location |	`gs://YOUR_PROJECT/temp`
> Replace `YOUR_PROJECT` with your project ID.
- Click **RUN JOB**.
- Click **Check my progress** to verify the objective

## Task 2: Run a simple Dataproc job
