## Part 1 start with 1 movie service
1. create venv and install uvicorn & fasapi and activate the venv

2. `uvicorn app.main:app --reload` (go to localhost:8000 for  app; localhost:8000/docs for docs)

3. `psql -h localhost -p 8081 -U postgres -W` (port cn be whichever docker port u use)

4. CREATE DATABASE movie_db; CREATE USER movie_user WITH ENCRYPTED PASSWORD 'movie_password'; GRANT ALL PRIVILEGES ON DATABASE movie_db TO movie_user;

5. (after you do all that above, get out) `psql -h localhost -p 8081 -U movie_user -W movie_password -d movie_db` (port cn be whichever docker port u use)

6. select * from movies;

---
## Part 2 orchestrate
1. docker-compose.yml builds the dbs and such, no env vars needed `docker-compose up -d`

2. http://localhost:8002/docs to add a cast in casts service. http://localhost:8001/docs to add the movie in the movie service.

---
## Part 3 nginx for host ease
1. add nginx to docker-compose and rebuild

2. head to  http://localhost:8080/api/v1/movies/

3. http://localhost:8080/api/v1/movies/docs for movie service docs and from http://localhost:8080/api/v1/casts/docs for casts service

