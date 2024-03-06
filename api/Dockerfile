FROM python:3.9

WORKDIR /app/

COPY ./requirements.txt ./

RUN Pip install uvicorn fastapi python-decouple

COPY  . .

CMD ["uvicorn", "app.main:app", '--host', "0.0.0.0", "--port", "8080"]