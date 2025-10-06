University: [ITMO University](https://itmo.ru/ru/) \
Faculty: [FTMI](https://ftmi.itmo.ru/) \
Course: [Introduction to WEB Technologies](https://my.itmo.ru/programs/38471?p=mainRPD) \
Year: 2025/2026 \ 
Group: U4225 \ 
Author: Barakhsin Grigorii Mikhailovich \
Lab: Lab0 \
Date of create: 03.10.2025 \
Date of finished: TBD 


## Docker installation
* Установить Docker Desktop (для Windows/Mac) или Docker Engine (для Linux)
* Проверить установку командой docker --version
* Запустить тестовый контейнер: docker run hello-world
![image](/data/lab1-docker_installation.png?raw=true)
* Изучить базовые команды: docker images, docker ps, docker ps -a
Docker installation part 2
![image](/data/lab1-docker_installation2.png?raw=true)

## Work with existing images
* Скачать образ Ubuntu: docker pull ubuntu:latest
* Запустить интерактивный контейнер: docker run -it ubuntu bash
![image](/data/lab1-docker_ubuntu_image.png?raw=true)
* Внутри контейнера установить пакет (например, curl): apt update && apt install -y curl
* Проверить установку: curl --version
![image](/data/lab1-docker_ubuntu_image_check.png?raw=true)
* Выйти из контейнера: exit

## Work with WEB-server

* Запустить контейнер с nginx: docker run -d -p 8080:80 --name web-server nginx:alpine
* Посмотреть логи контейнера: docker logs web-server
![image](/data/lab1-docker_nginx_web.png)
* Проверить работу в браузере: http://localhost:8080

![image](/data/lab1-docker_nginx_web2.png)
* Подключиться к контейнеру: docker exec -it web-server sh

## Container management

* Посмотреть запущенные контейнеры: docker ps
* Посмотреть все контейнеры: docker ps -a
* Остановить контейнер: docker stop web-server
* Запустить остановленный контейнер: docker start web-server
* Удалить контейнер: docker rm web-server
* Удалить образ: docker rmi nginx:alpine
![image](/data/lab1-docker_container_management.png)

## Work with volumes

* Создать том: docker volume create my-volume
* Запустить контейнер с томом: docker run -it --name volume-test -d -v my-volume:/data ubuntu bash
* Подключиться к контейнеру: docker exec -it volume-test bash
* Создать файл в томе: echo "Hello from volume" > /data/test.txt
* Удалить контейнер и создать новый с тем же томом
* Проверить, что файл сохранился
![image](/data/lab1-docker_volume_management.png)