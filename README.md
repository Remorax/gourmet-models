# Gourmet Models

## Overview
The [Gourmet](https://gourmet-project.eu) project has released several machine translation models to translate low-resource languages. This repository
contains information about the models, as well as sample code showing how the models can be used. The models themselves are available as dockers, and
can be downloaded from a separate site (see below).

Some of the models are described in our public deliverables. See the [integration report](https://gourmet-project.eu/wp-content/uploads/2020/07/GoURMET_D5_3_Initial_Integration_Report.pdf) for details of model training, and the [evaluation report](https://gourmet-project.eu/wp-content/uploads/2020/07/GoURMET_D5_4___Initial_Evaluation-2.pdf) for details of evaluation. 


## Using the Models

The model download links are [here](https://github.com/EdinburghNLP/gourmet-models/blob/main/models.md). Once downloaded, the model
can be deployed using:
```
docker load < <MODEL_FILE>
```
to launch the translation server, use:

```
docker run -p 4000:4000 -i --rm <MODEL_NAME>
```
This exposes the model on port 4000. Change the second number above if you want to use a different port.

To test the model, use the [sample client](https://github.com/EdinburghNLP/gourmet-models/blob/main/sample-client/gourmet-client.py) like this:

```
$ ./gourmet-client.py 
2021-11-15 14:54:10 DEBUG: __main__:  Connecting to translation server at localhost4000
2021-11-15 14:54:10 DEBUG: urllib3.connectionpool:  Starting new HTTP connection (1): localhost:4000
2021-11-15 14:54:14 DEBUG: urllib3.connectionpool:  http://localhost:4000 "POST /translation HTTP/1.1" 200 88
Translation: An gudanar da taron sauyin yanayi a Glasgow
Time: 2242
Error: None
```
This is using the English to Hausa model. You can use the `-n` and `-p` arguments to change the host and port. The source text is hard-coded but easily changed.

Some of the models support additional arguments which can be passed to the docker at launch time, using the `-e` argument to docker (for environemnent) variables. See the models page for more details.

## Computational Requirements
All models are configured to use the CPU for translation. A GPU is not required, and the models will not use it.

## Licence

CC-BY

## Acknowledgements
This project has received funding from the European Union’s Horizon 2020 research and innovation programme under grant agreement No 825299.


