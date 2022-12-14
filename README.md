# Description
This applied data science project was completed as part of the "Practical Data Science on the AWS Cloud Specialization" offered by AWS and DeepLearning.ai. The focus of the specialization is to develop the skills needed to move ML projects from development to production. The specialization is conducted in 3 parts and an overview is described below. The dataset was obtained from Kaggle with 23,000 customer reviews and ratings on Women's E-commerce clothing, and is shared in a public Amazon S3 bucket.

### Part 1: Analyzing Dataset and Train ML Models using Auto ML
- Ingested and transformed the [public dataset](https://www.kaggle.com/nicapotato/womens-ecommerce-clothing-reviews), before registering the S3 dataset files as a table for querying on the AWS Glue Catalog
- Run SQL queries using Amazon Athena to do EDA and visualization
- Analyze the class imbalance on dataset with Amazon SageMaker Clarify
- Balance the dataset by product category and sentiment, then evaluate the bias report based on the `Class Imbalance (CI)` and `Difference in Positive Proportions in Labels (DPL)` metrics
- Use SageMaker AutoPilot and **AutoML** to train three BERT-based NLP models to analyze customer feedback and classify messages into positive (+1), negative (-1), and neutral (0) sentiment, finally deploying the best candidate model as a REST Endpoint
- Use SageMaker **BlazingText** (a variant of FastText which is based on word2vec) built-in algorithm to predict the sentiment for each customer review

### Part 2: Build, Train and Deploy ML Pipeline using BERT
- Configure an Amazon SageMaker processing job to perform required feature transformation to convert original review text into BERT-readable features
- Store the BERT-readable features into Feature Store
- Finetune a text classifier using Hugging Face's pre-trained model, a BERT variant called [RoBERTa](https://huggingface.co/roberta-base)  within a PyTorch model ran as a SageMaker Training Job
- Build a SageMaker Pipeline to evaluate the model's accuracy and only deploy model if accuracy exceeds given threshold
- Automate the end-to-end machine learning workflow and tracking artifacts and model lineage through the pipeline

### Part 3: Optimize ML Models and Deploy Human-in-the-Loop Pipelines
- Tune text-classifier using Automated Hyperparameter Tuning (HPT) with Random tuning strategy
- Configure and create REST endpoint with multiple variants to split traffic
- Deploy two candidates into A/B testing to compare real-time prediction performance
- Shift traffic to one of the variants and configure it to autoscale
- Set up Amazon Cognito user pool and Human Task UI and define human review workflow to perform data labelling
- Deploy custom ML model into an endpoint, then fix misclassified predictions and generate new training data using Amazon Augmented AI
