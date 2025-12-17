✅ FULL STEP-BY-STEP NOTES (from scratch to working system) 

Flask App + Redis + Dockerfile + Docker Compose 

 
 

1️⃣ Project Setup 

Why: Keep everything organised in a single directory. 

Commands 

mkdir flask_redis_app 
cd flask_redis_app 
python3 -m venv venv 
source venv/bin/activate     # Windows: venv\Scripts\activate 
 

 
 

2️⃣ Install Dependencies 

Why: Flask = web server, Redis package = Python client. 

pip install flask redis 
 

 
 

3️⃣ Create requirements.txt 

Why: Docker will install everything from this file. 

flask 
redis 
 

 
 

4️⃣ Create app.py 

Purpose: 

Flask app with two routes: 

/ → welcome message 

/count → increments Redis key "visits" 

Concepts in this file 

Import Flask, Redis, OS 

Read environment variables (REDIS_HOST, REDIS_PORT) 

Create Redis client 

Define two routes 

Run Flask on 0.0.0.0:5000 

Final structure (copy this into app.py) 

from flask import Flask 
import redis 
import os 
 
app = Flask(__name__) 
 
# Get Redis host/port from environment 
redis_host = os.getenv("REDIS_HOST", "localhost") 
redis_port = int(os.getenv("REDIS_PORT", 6379)) 
 
# Create Redis client 
r = redis.Redis(host=redis_host, port=redis_port, decode_responses=True) 
 
@app.route('/') 
def home(): 
    return "Welcome to Flask + Redis!" 
 
@app.route('/count') 
def count(): 
    new_count = r.incr("visits") 
    return f"Visit count: {new_count}" 
 
if __name__ == '__main__': 
    app.run(host="0.0.0.0", port=5000) 
 

 
 

5️⃣ Create Dockerfile 

Purpose: 

Defines how to build your Flask app as a Docker image. 

Put this in Dockerfile: 

FROM python:3.9 
WORKDIR /usr/src/app 
COPY requirements.txt . 
RUN pip install --no-cache-dir -r requirements.txt 
COPY . . 
EXPOSE 5000 
CMD ["python", "app.py"] 
 

 
 

6️⃣ Create docker-compose.yml 

Purpose: 

Runs Flask app + Redis together in one command. 
Docker Compose automatically creates a network, so Flask can reach Redis via hostname redis. 

Put this in docker-compose.yml: 

version: "3.9" 
 
services: 
  redis: 
    image: redis:7-alpine 
    ports: 
      - "6379:6379" 
 
  web: 
    build: . 
    ports: 
      - "5000:5000" 
    environment: 
      REDIS_HOST: redis 
      REDIS_PORT: 6379 
    depends_on: 
      - redis 
 

 
 

7️⃣ Build and Run Everything 

One command starts everything: 

docker compose up --build 
 

You should see: 

Redis logs 

Flask logs saying Running on 0.0.0.0:5000 

 
 

8️⃣ Test the Application 

In browser or curl: 

Home route 

http://localhost:5000/ 
 

Count route 

http://localhost:5000/count 
 

Each refresh → number should increase: 

Visit count: 1 
Visit count: 2 
Visit count: 3 
... 
 

 
 

9️⃣ Optional: Check Redis Value 

docker compose exec redis redis-cli 
GET visits 
 

 
 

🔟 Stop Everything 

docker compose down 
 

 
 

⭐ SUMMARY OF ALL COMMANDS 

mkdir flask_redis_app 
cd flask_redis_app 
python3 -m venv venv 
source venv/bin/activate 
pip install flask redis 
docker compose up --build 
docker compose down 
docker compose exec redis redis-cli 
 

 
