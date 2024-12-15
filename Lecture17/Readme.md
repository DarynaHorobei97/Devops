1. Завантажила Docker на Windows
2. Створила docker-compose.yml
3. 
docker-compose up -d

docker-compose ps


![Image1](images/Lecture17/Terminal 2024-12-15 17.28.54.png)

![Image1](images/Lecture17/ContainersDockerDesktop.png)
![Image1](images/Lecture17/ImagesDockerDesktop.png)

![Image1](images/Lecture17/Welcometonginx.png)


4. Налаштування мережі й томів
   docker network ls
   docker volume ls

![Image1](images/Lecture17/Terminal 2024-12-15 17.32.46.png)
![Image1](images/Lecture17/Terminal 2024-12-15 17.33.05.png)


5. Масштабування сервісів
Секцію ports видаляємо з web, оскільки Docker не може призначити різні порти 
для одного сервісу при масштабуванні автоматично.

![Image1](images/Lecture17/Terminal 2024-12-15 17.39.27.png)

docker-compose ps
![Image1](images/Lecture17/Terminal 2024-12-15 17.40.14.png)
