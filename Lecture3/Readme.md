Створюю VM з 2 ГБ оперативної пам'яті:
![Image1](images/image1.png)

Створюю новий віртуальний жорсткий диск розміром 20 ГБ у форматі VDI:
![image2](images/image2.png)

Обираю процесор на 2 ядра:
![image4](images/image4.png)

Завершена інсталяція VM:
![afterInstall](images/afterInstall.png)

Створюю знімок VM:
![image8](images/image8.png)

Створюю файл:
![image10](images/image10.png)

Роблю рестор знімку, переконуюся, що файла немає:
![image11](images/image11.png)

Вимикаю VM і встановлюю новий розмір диску (30 ГБ):
![add30gb](images/add30gb.png)
Я не знайшла можливості зробити resize поточного диску, в Storage не було опції resize, попередньо встановлені 20 gb тільки на перегляд доступні, вийшло тільки створити новий із 30 gb. Потім VM пішла на переустановку.

Стан файлової системи:
![image17](images/image17.png)


Processor збільшую кількість ядер CPU на 4, а у вкладці Motherboard збільшую обсяг оперативної пам'яті на 4 ГБ:
![image14](images/image14.png)
![image13](images/image13.png)

Далі видаляю VM (delete all files):
![VirtualBox](images/VirtualBox.png)
