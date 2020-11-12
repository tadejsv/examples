<p align="center">
 
[![Jina](https://github.com/jina-ai/jina/blob/master/.github/badges/jina-badge.svg "We fully commit to open-source")](https://jina.ai)
[![Jina](https://github.com/jina-ai/jina/blob/master/.github/badges/jina-hello-world-badge.svg "Run Jina 'Hello, World!' without installing anything")](https://github.com/jina-ai/jina#jina-hello-world-)
[![Jina](https://github.com/jina-ai/jina/blob/master/.github/badges/license-badge.svg "Jina is licensed under Apache-2.0")](#license)
[![Jina Docs](https://github.com/jina-ai/jina/blob/master/.github/badges/docs-badge.svg "Checkout our docs and learn Jina")](https://docs.jina.ai)
[![We are hiring](https://github.com/jina-ai/jina/blob/master/.github/badges/jina-corp-badge-hiring.svg "We are hiring full-time position at Jina")](https://jobs.jina.ai)
<a href="https://twitter.com/intent/tweet?text=%F0%9F%91%8DCheck+out+Jina%3A+the+New+Open-Source+Solution+for+Neural+Information+Retrieval+%F0%9F%94%8D%40JinaAI_&url=https%3A%2F%2Fgithub.com%2Fjina-ai%2Fjina&hashtags=JinaSearch&original_referer=http%3A%2F%2Fgithub.com%2F&tw_p=tweetbutton" target="_blank">
  <img src="https://github.com/jina-ai/jina/blob/master/.github/badges/twitter-badge.svg"
       alt="tweet button" title="👍Share Jina with your friends on Twitter"></img>
</a>
[![Python 3.7 3.8](https://github.com/jina-ai/jina/blob/master/.github/badges/python-badge.svg "Jina supports Python 3.7 and above")](#)
[![Docker](https://github.com/jina-ai/jina/blob/master/.github/badges/docker-badge.svg "Jina is multi-arch ready, can run on differnt architectures")](https://hub.docker.com/r/jinaai/jina/tags)

</p>

# Multimodal Search With TIRG
In this example we make a multimodal search engine using [TIRG](https://github.com/google/tirg)(Composing Text and Image for Image Retrieval). We are using the Fashion200k dataset for this. In multimodal search engines we give more than one modalities at the input. Over here we give a cloth image and text as input. The model constructs feature embedding using both the inputs which is used for searching over the indexed images.

<p align="center">
  <img src=".readme_images/fashion200k.png?raw=true" alt="Jina banner" width="70%">
</p>
<p align="center">
  <img src="https://github.com/google/tirg/blob/master/images/newpipeline.png?raw=true" alt="Jina banner" width="70%">
</p>
**Table of Contents**

- [Download and Extract Data](#download-and-extract-data)
- [Build Encoder Images](#build-encoder-images)
- [Index Image Data](#index-image-data)
- [Query](#query)
- [Troubleshooting](#troubleshooting)
- [Documentation](#documentation)
- [Community](#community)
- [License](#license)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Download and Extract Data
You can try this example with [Fashion200k](https://github.com/xthan/fashion-200k) dataset.

[Download](https://drive.google.com/drive/folders/0B4Eo9mft9jwoamlYWFZBSHFzV3c) and extract it in data folder in this example folder.

## Build encoder images
This will download the TIRG model + code and build the image
### TIRG image encoder
Start the Docker. Go to TirgImageEncoder folder and run the below command  
`docker build -f Dockerfile -t jinaai/hub.executors.encoders.image.tirg .`
### TIRG multimodal encoder
Start the Docker. Go to TirgMultimodalEncoder folder and run the below command  
`docker build -f Dockerfile -t jinaai/hub.executors.encoders.multimodal.tirg .`

## Index Image Data
Index 1000 images. This can take some time and you can try a smaller number as well.
```bash
python app.py -task index -n 1000 -overwrite True
```

If it's running successfully, you should be able to see logs scrolling in the console and in the dashboard:

<p align="center">
  <img src="https://github.com/jina-ai/jina/blob/master/.github/.README_images/0a8863abb3fcee182e1fe8fe46c47b7a.gif?raw=true" alt="Jina banner" width="45%">
  <img src="https://github.com/jina-ai/jina/blob/master/.github/.README_images/ed2907cd11ac26a2a3a2555f16071d13.gif?raw=true" alt="Jina banner" width="45%">
</p>

## Query
This will start the server, run your query and give result as a pop-up.
```bash
python app.py -task query --image_path path_to_image --text_query 'change color to red'
```

## Troubleshooting

### Memory Issues

If you are using Docker Desktop, make sure to assign enough memory for your Docker container, especially when you have multiple replicas. Below are my MacOS settings with two replicas:


<p align="center">
  <img src="https://github.com/jina-ai/jina/blob/master/.github/.README_images/d4165abd.png?raw=true" alt="Jina banner" width="80%">
</p>

## Documentation 

<a href="https://docs.jina.ai/">
<img align="right" width="350px" src="https://github.com/jina-ai/jina/blob/master/.github/jina-docs.png" />
</a>

The best way to learn Jina in depth is to read our documentation. Documentation is built on every push, merge, and release event of the master branch. You can find more details about the following topics in our documentation.

- [Jina command line interface arguments explained](https://docs.jina.ai/chapters/cli/index.html)
- [Jina Python API interface](https://docs.jina.ai/api/jina.html)
- [Jina YAML syntax for executor, driver and flow](https://docs.jina.ai/chapters/yaml/yaml.html)
- [Jina Protobuf schema](https://docs.jina.ai/chapters/proto/index.html)
- [Environment variables used in Jina](https://docs.jina.ai/chapters/envs.html)
- ... [and more](https://docs.jina.ai/index.html)

## Community

- [Slack channel](https://join.slack.com/t/jina-ai/shared_invite/zt-dkl7x8p0-rVCv~3Fdc3~Dpwx7T7XG8w) - a communication platform for developers to discuss Jina
- [Community newsletter](mailto:newsletter+subscribe@jina.ai) - subscribe to the latest update, release and event news of Jina
- [LinkedIn](https://www.linkedin.com/company/jinaai/) - get to know Jina AI as a company and find job opportunities
- [![Twitter Follow](https://img.shields.io/twitter/follow/JinaAI_?label=Follow%20%40JinaAI_&style=social)](https://twitter.com/JinaAI_) - follow us and interact with us using hashtag `#JinaSearch`  
- [Company](https://jina.ai) - know more about our company, we are fully committed to open-source!

## License

Copyright (c) 2020 Jina AI Limited. All rights reserved.

Jina is licensed under the Apache License, Version 2.0. See [LICENSE](https://github.com/jina-ai/jina/blob/master/LICENSE) for the full license text.