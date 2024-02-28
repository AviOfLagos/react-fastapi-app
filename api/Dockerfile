FROM python:3.10-alpine
WORKDIR /app
COPY . /app
RUN pip install -r requirements.txt
EXPOSE 8000
ENV HNG_API_HOST=0.0.0.0
ENV HNG_API_ORIGINS=http://localhost:3000
CMD ["python", "main.py"]
                         
