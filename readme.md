# Recorded Steps

### Set up linux
- Allow command history
```sh
sudo chown $USER:$USER ~/.bash_history
sudo chmod u+w ~/.bash_history
```

### Set up Docker

```sh
sudo apt install docker.io
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
docker run hello-world
```

pipeline.py
```python
import pandas as pd
import sys

print(sys.argv)
day = sys.argv[1]
print(f"Day provided: {day}")
print('Job finished')
```

Dockerfile
```docker
FROM python:3.9

RUN pip install pandas
WORKDIR /app
COPY pipeline.py pipeline.py
ENTRYPOINT [ "python", "pipeline.py" ]
```

```sh
docker build -t python-test .
docker run -it python-test
```

Postgres
```sh
docker run -it \
    -e POSTGRES_USER="root" \
    -e POSTGRES_PASSWORD="root" \
    -e POSTGRES_DB="ny_taxi" \
    -v $(pwd)/ny_taxi_postgres_data:/var/lib/postgresql/data \
    -p 5432:5432 \
    postgres:13
```

```sh
sudo apt install pgcli
```