/ touch Dockerfile  

 

FROM python:3.8-slim 

WORKDIR /app 

COPY . . 

RUN pip install flask 

EXPOSE 5000 

CMD ["python", "app.py"] 

 

 

 

Create dockerfile ,  then dockerimage , then container 

 

RUN:  

docker run -d -p 5000:5000 hello-flask 

 

docker stop ID 

 

 

 
