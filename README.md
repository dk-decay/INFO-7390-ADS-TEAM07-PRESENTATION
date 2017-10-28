=============================================
1. ENVIRONMENT SETUP - Python 2.7 needed
=============================================

Reference URL : https://github.com/GoogleCloudPlatform/cloudml-samples/tree/master/census/keras


a. Install google cloud sdk on your local machine
b. Create a virtual environment and do a pip install --upgrade -r requirements.txt, which installs keras, tensorflow and other basic python dependencies
c. Execute steps explained below.



=============================================
2. FOR TRAINING THE MODEL AND SAVING IT ON DISC
=============================================

<path to google-cloud-sdk>/google-cloud-sdk/bin/gcloud ml-engine local train --package-path trainer \
                             --module-name trainer.task \
                             -- \
                             --train-files adult.data.csv \
                             --eval-files adult.test.csv \
                             --job-dir census_output \
                             --train-steps 200


===========================================
3. CREATING A SAMPLE REQUEST JSON FOR PREDICTION
===========================================

python preprocess.py sample.json


===========================================
4. USING GOOGLE CLOUD TO PREDICT
===========================================

<path to google-cloud-sdk>/google-cloud-sdk/bin/gcloud ml-engine local predict --model-dir=census_output/export \
                               --json-instances sample.json
