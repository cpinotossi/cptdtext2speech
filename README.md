# Azure Text to speech demo

## Azure Text to speech demo with node.js

based on https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started-text-to-speech?tabs=terminal&pivots=programming-language-javascript

~~~ bash
npm install microsoft-cognitiveservices-speech-sdk
code SpeechSynthesis.js
prefix=cptdtext2speech
location=eastus
az group create -n $prefix --location $location
az cognitiveservices account create --kind SpeechServices -n $prefix -l $location -g $prefix --sku S0 --yes 
az resource list -g $prefix -o table
key=$(az cognitiveservices account keys list -g $prefix -n $prefix --query key1 -o tsv)
npm start $key $location testblabla
./testblabla.wav # you will need to install software which does play wav files
~~~

~~~ bash
# clean up
az group delete -n $prefix -y # delete resources.
az cognitiveservices account purge -n $prefix -l $location -g $prefix # delete account which is soft delete protected.
~~~


# misc

## cognitiveservices

~~~ bash

~~~
## gh, git tips and tricks

~~~ bash
gh repo create $prefix --public
git remote add origin https://github.com/cpinotossi/$prefix.git
git status
git add *
git commit -m"initial commit"
git push origin main 
~~~