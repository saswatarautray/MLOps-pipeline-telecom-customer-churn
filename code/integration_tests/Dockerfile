FROM python:3.9.12

RUN pip install -U pip
RUN pip install pipenv

WORKDIR /app

COPY requirements.txt requirements.txt

COPY [ "Pipfile" , "Pipfile.lock", "./"]

RUN pip3 install -r requirements.txt

RUN pip3 install pyarrow

COPY churn_prediction.py . 

COPY model.pkl .

ENTRYPOINT ["gunicorn", "--bind=0.0.0.0:9696", "churn_prediction:app"]