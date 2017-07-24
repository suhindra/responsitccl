#### Jekyll Static Page
1 Folder apps merupakan web stastis (Jekyll Pages) yang di clone dari repo https://github.com/suhindra/suhindra.github.io

#### Dockerfile
Dockerfile ini digunakan untuk membangun image docker. Dockerfile tersebut menggunakan image ruby:latest dan berisi perintah-perintah yang perintah-perintah yang diperlukan untuk mengelola jekkyl. Untuk menjalankan Jekyll Pages di docker, gunakan image (suhindra/jekyll-container), 

#### Docker Compose

Untuk `docker-compose` via `docker-compose.yml`,image untuk membuat container dari docker image (suhindra/jekyll-container:latest) volume untuk menunjukan diretory dari jekyll site saya, port untuk mengarahkan port host  4000 ke port container  4000 (4000:4000),

`docker-compose.yml`:

docker-compose.yml:

```yml
jekyll-container:
    image: suhindra/jekyll-container
    ports:
        - "4000:4000"
    volumes:
        - /var/www/html/suhindra.github.io:/code
    working_dir: /code   
```


Untuk menjalankan docker-compose:

```bash
alisancatur@alisancatur-Lenovo-Z40-75:~/jekyll-container$docker-compose up
Recreating jekyllcontainer_jekyll-container_1 ... 
Recreating jekyllcontainer_jekyll-container_1 ... done
Attaching to jekyllcontainer_jekyll-container_1
jekyll-container_1  | Configuration file: /code/_config.yml
jekyll-container_1  | Configuration file: /code/_config.yml
jekyll-container_1  |             Source: /code
jekyll-container_1  |        Destination: /code/_site
jekyll-container_1  |  Incremental build: disabled. Enable with --incremental
jekyll-container_1  |       Generating... 
jekyll-container_1  |                     done in 1.294 seconds.
jekyll-container_1  |  Auto-regeneration: enabled for '/code'
jekyll-container_1  | Configuration file: /code/_config.yml
jekyll-container_1  |     Server address: http://0.0.0.0:4000/
jekyll-container_1  |   Server running... press ctrl-c to stop.
```

Jika mengakses http://0.0.0.0:4000 di browser terlihat seperti

