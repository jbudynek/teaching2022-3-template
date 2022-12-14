# Practicing packaging, containerization and monitoring

This file is a step by step tutorial to practice basics of app packaging, containerization and monitoring. See working example at: https://github.com/jbudynek/teaching2022-3-working-example

## Core app and FastAPI
- prepare your virtual environment
```
conda create --name 221203_enseirb --clone base
conda activate 221203_enseirb
```

- the file structure: 
  - `app` - holds python code for our application
  - `Dockerfile` - holds docker directive for containerization
  - `requirements.txt` - hold list of python libs, make sure to keep it up to date during development

```
.
├── Dockerfile
├── app
│   ├── __init__.py
│   ├── main.py
│   └── model.py
└── requirements.txt
```


- write model instantiation code
  - in `app/model.py`, write training code
- write prediction code
  - in `app/model.py`, write prediction code
- test this code

- wrap it in FastAPI
  - in `app/main.py`, create endpoints that call the methods of `model.py`
- try it in a fresh conda environment
  - go to docs `http://localhost:5000/do`
  - with `curl`

```
conda activate 221203_enseirb
pip install -r requirements.txt
python app/main.py
```

## Docker

- write your `Dockerfile`
  - choose base image
  - install requirements
  - copy app files
  - start uvicorn server
- Build
- Run
- challenge = smallest docker image

```
docker build -t fastapiml .
docker run -d --name fastapiml-app -p 5000:5000 fastapiml
```

## Monitoring
- in `model.py`
  - create a way to store features and predictions (in a list)
  - create a function to plot training data distribution and stored data distribution
- in `main.py` 
  - modify predict endpoint to also call storage function in model
  - create endpoint to produce plot


## Misc helpful links
- HOWTO FastAPI and Docker example with TensorFlow 
  - https://www.quantmetry.com/blog/tutoriel-deployer-api-machine-learning/
- HOWTO FastAPI and Docker example with scikit-learn
  - https://towardsdatascience.com/how-to-prepare-scikit-learn-models-for-production-4aeb83161bc2
- HOWTO use Random Forest to classify Iris dataset
  - https://www.blopig.com/blog/2017/07/using-random-forests-in-python-with-scikit-learn/
- FastAPI doc: https://fastapi.tiangolo.com/
- Uvicorn website: https://www.uvicorn.org/
- Tensofrflo website: https://www.tensorflow.org/
- Docker overview: https://docs.docker.com/get-started/overview/
- Evidently AI website: https://www.evidentlyai.com/

