# GSP092 
>🚨 [PLEASE SUBSCRIBE OUR CHANNEL CLOUDHUSTLER](https://www.youtube.com/@cloudhustlers) **&** [JOIN OUR WHATSAPP COMMUNITY](https://chat.whatsapp.com/FilXyp4eva599SND76fNUP)
## Run in Cloudshell
```cmd
export REGION=
```
```cmd
cat <<EOF> function.js
exports.helloWorld = (req, res) => {
  res.status(200).send('Hello, Hustlers!');
};
EOF
gcloud functions deploy helloWorld \
  --runtime nodejs16 \
  --trigger-http \
  --allow-unauthenticated \
  --region $REGION \
  --max-instances 5
gcloud logging metrics create CloudFunctionLatency-Logs \
    --project=$DEVSHELL_PROJECT_ID \
    --description="Metric for Cloud Function latency" \
    --log-filter='resource.type="cloud_function"
resource.labels.function_name="helloWorld"'
```
