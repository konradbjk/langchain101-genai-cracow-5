# ​Langchain 101: Building Generative AI Apps in python
This repo contains, code that was presented during [GenAI Cracow #5](https://lu.ma/vterj1l9)

**Presentation details**
Curious about Generative AI but not sure where to begin? Langchain makes it easier than ever to build AI products. In this talk, Konrad will explain the Langchain framework building blocks and why it stands out. You will learn how to mix and match components like prompts, models, retrievers, memory, and agents to build AI-powered applications that engage and delight your users.

Sure! Here's a table of contents for the GitHub readme:  
   
1. [Installation](#installation)  
   - [Related to python](#related-to-python)  
   - [Docker setup for Qdrant](#docker-setup-for-qdrant)  
   - [Environment Variables](#environment-variables)  
   - [(Optional) Langsmith](#optional-langsmith)  
2. [Usage](#usage)  
   - [Supplying data](#data)  
3. [Working on a Generative AI project?](#working-on-a-generative-ai-project)  
   
## Installation

## Related to python
We are using poetry to manage packages, and conda to manage python virtual environments

Follow this guide to install [conda](https://conda.io/docs/user-guide/install/)

Once you have conda installed, we can create a new venv on conda using
```bash
conda env create -f environment.yml
```

**Remember to keep the conda's environment.yml file clean, we keep dependencies on poetry.** In this project, we are using python `3.10.14`. If you need to upgrade python or poetry version - upgrade those in the `environment.yml` and recreate the environment.

We store the project python configuration in `pyproject.toml`
Especially python version
```
[tool.poetry.dependencies]
python = "^3.10"
```

Run below command to install all dependencies
```bash
poetry install
```

Make sure the right python interpreter is selected

```bash
conda activate your_env_name
which python
poetry run which python
poetry shell
which python
```

### Docker setup for Qdrant
I balieve that the easiest and fastest way to spin qdrant locally is via docker. If you do not have docker installed, please follow [Docker's official guide](https://docs.docker.com/engine/install/). While Docker Desktop works fine on macOS, I have received feedback, that it does not run well with Windows.

While installing qdrant as a docker, make sure to download `v1.10.1`, as this is the version, I have used. You might try to upgrade, but it might require code changes
```bash
docker pull qdrant/qdrant:v1.10.1
```

No use `docker run` 
```bash
docker run -p 6333:6333 -p 6334:6334 \
    -v $(pwd)/qdrant_storage:/qdrant/storage \
    qdrant/qdrant
```
or `docker compose up -d` to start the qdrant container. 

Now you should be able to access it's UI in a browser using [localhost:6333/dashboard](http://localhost:6333/dashboard).

Please check the [official guide of qdrant local deployment](https://qdrant.tech/documentation/quickstart/) in case of issues.

### Environment Variables
Copy `.env.template` and fill it with the secrets according to your needs. Save the file as `.env`

*If you are using Windows, you might expect issues with the envirnment variables, due to how Windows manages those.*

### (Optional) Langsmith
In the env template, you could find properties for Langsmith. I am affiliated neither with Langchain nor Langsmith. I have been one of the beta testers, and I implement it with most of my customers. If you would like to learn more about Langsmith, check [their website](https://www.langchain.com/langsmith).

You can also check the [official walkthrough to Langsmith](https://docs.smith.langchain.com/).

## Usage
Now head over to `langchain-intro.ipynb` file, select the python kernel to the conda env. 

You can read more on how to use jupyter notebook on [VS Code's docummentation](https://code.visualstudio.com/docs/datascience/jupyter-notebooks)

### Data
During the session, I have used transcodings from [webinars I host with Adam](https://lu.ma/budowanie-produktow-ai). Those are not part of the repo. You can use any other text files in this case, or contact me on [LinkedIn](https://www.linkedin.com/in/konrad-bujak/), and I can share with you some of the transcodings.

I have left for you the ebook, I created some time ago with my colleague. This ebook was created using Canva, and we exported it in a way, that it is impossible to be mined ([more about parsing PDFs with Langchain v0.2](https://python.langchain.com/v0.2/docs/how_to/document_loader_pdf/)). In this case, you would need to work with OCR.

## Working on a Generative AI project?
If you are working on a GenAI project, let me know, I might help. I am working as a private consultant for companies who want to build AI-based products. I connect my Software Engineering experience (including Generative AI Engineering) with my Product Management skills. We can discuss what and how to build, alongside why to build it, and what would be the ROI.
Feel free to reach out to [me on LinkedIn](https://www.linkedin.com/in/konrad-bujak/)