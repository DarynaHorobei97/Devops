Створюю VM з 2 ГБ оперативної пам'яті:
![image (2).png](..%2F..%2FDownloads%2Fhw3%2Fimage%20%282%29.png)

Створюю новий віртуальний жорсткий диск розміром 20 ГБ у форматі VDI:
![image (3).png](..%2F..%2FDownloads%2Fhw3%2Fimage%20%283%29.png)

Обираю процесор на 2 ядра:
![image (4).png](..%2F..%2FDownloads%2Fhw3%2Fimage%20%284%29.png)

Завершена інсталяція VM:
![afterInstall.png](..%2F..%2FDownloads%2Fhw3%2FafterInstall.png)

Створюю знімок VM:
![image (8).png](..%2F..%2FDownloads%2Fhw3%2Fimage%20%288%29.png)

Створюю файл:
![image (10).png](..%2F..%2FDownloads%2Fhw3%2Fimage%20%2810%29.png)

Роблю рестор знімку, переконуюся, що файла немає:
![testvm5 (ss27112024) [Running] - Oracle VirtualBox.png](..%2F..%2FDownloads%2Fhw3%2Ftestvm5%20%28ss27112024%29%20%5BRunning%5D%20-%20Oracle%20VirtualBox.png)

Вимикаю VM і встановлюю новий розмір диску (30 ГБ):
![add30gb.png](..%2F..%2FDownloads%2Fhw3%2Fadd30gb.png)
Я не знайшла можливості зробити resize поточного диску, в Storage не було опції resize, попередньо встановлені 20 gb тільки на перегляд доступні, вийшло тільки створити новий із 30 gb. Потім VM пішла на переустановку.

Стан файлової системи:
![image (17).png](..%2F..%2FDownloads%2Fhw3%2Fimage%20%2817%29.png)


Processor збільшую кількість ядер CPU на 4, а у вкладці Motherboard збільшую обсяг оперативної пам'яті на 4 ГБ:
![image (14).png](..%2F..%2FDownloads%2Fhw3%2Fimage%20%2814%29.png)
![image (13).png](..%2F..%2FDownloads%2Fhw3%2Fimage%20%2813%29.png)

Далі видаляю VM (delete all files):
![VirtualBox - Question 2024-11-27 18.59.45.png](..%2F..%2FDownloads%2Fhw3%2FVirtualBox%20-%20Question%202024-11-27%2018.59.45.png)