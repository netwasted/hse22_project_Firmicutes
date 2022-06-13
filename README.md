# Проект по майнору "Биоинформатика"
## Таксон бактерий: Firmicutes
## Род бактерий: Clostridium (индивидуальная часть)

### Ссылка на ноутбук с кодом

https://colab.research.google.com/drive/123m8zV2-Ka4hRH78nO4RkrdP286L-pad?usp=sharing

### Сводная таблица по геномам

|index|Название вида|Количество скаффолдов|Количество хромосом|Количество плазмид|Общая длина последовательностей \(Mb)|Количество аннотированных генов|Доля аннотированных генов в геноме|Кол-во предсказанных участков Z-dna|Кол-во участков с zh-score &gt;500|Общая длина участков с zh-score &gt;500|
|---|---|---|---|---|---|---|---|---|---|---|
|0|Clostridium aceticum|2|1|1|4\.20704|3874|0\.8462184814026014|4201318|216|2432|
|1|Clostridium botulinum A str\. ATCC 3502|2|1|1|3\.90326|3566|0\.8162233620102171|3886916|205|2267|
|2|Clostridium cochlearium|1|1|0|2\.43542|2337|0\.8656285158206798|2435419|93|1015|
|3|Clostridium novyi|3|1|2|2\.49908|2302|0\.8511668293932168|2296219|156|1738|
|4|Clostridium septicum|2|1|1|3\.40472|3098|0\.8484932681688949|3399422|114|1316|

### Гистограммы значений ZH-Score

![image](https://user-images.githubusercontent.com/60008375/172836241-6f13e958-683e-4817-8380-b38fdd188c0d.png)

![image](https://user-images.githubusercontent.com/60008375/172836273-ef6046bc-b8da-4b2b-bb5f-fed2297161f0.png)

![image](https://user-images.githubusercontent.com/60008375/172836312-e24bd3de-8441-4a0c-8927-d659b1c854e6.png)

![image](https://user-images.githubusercontent.com/60008375/172836346-f9d10696-3aa2-4a14-9040-efdb02858575.png)

![image](https://user-images.githubusercontent.com/60008375/172836365-c0a15be5-c19b-4f16-a5c2-eafb26e52c07.png)

### Визуализация генов и предсказанных участков Z-DNA

**Clostridium aceticum**
![image](https://user-images.githubusercontent.com/60008375/173431600-fd4a005f-2b98-4401-93fa-693945424a21.png)

**Clostridium botulinum A str\. ATCC 3502**
![image](https://user-images.githubusercontent.com/60008375/173431653-c1c4a048-452d-4d0c-b168-63e1f067cb42.png)

**Clostridium cochlearium**
![image](https://user-images.githubusercontent.com/60008375/173431688-13334945-8d1c-4cc8-aaff-91c40eabf8dc.png)

**Clostridium novyi**
![image](https://user-images.githubusercontent.com/60008375/173431719-214d92eb-43d6-49bb-8111-3f64539d97c7.png)

**Clostridium septicum**
![image](https://user-images.githubusercontent.com/60008375/173431752-9e37f9a4-04f4-431a-95ec-a485dca10507.png)

### Информация по полученным гомологичным кластерам

**Количество кластеров:** 2729

**Гистограмма кластеров по кол-ву разных геномов в кластере**

![image](https://user-images.githubusercontent.com/60008375/173226721-ce4a84ac-21ba-4076-b452-5dcbb5b33bee.png)

**Таблица с информацией по выбранным кластерам**

Описание алгоритма отбора кластеров (код в ноутбуке): чтобы определить "хороший" кластер, будем смотреть для каждого белка, есть ли он в файлике пересечений Z-DNA и промотера соответствующего организма. Ранее для каждого промотера в файлик мы также вписывали имя белка, кодируемого генов данного промотера, поэтому эта информация нам сейчас пригодилась.

Несмотря на тщательный отбор генов, консервативные обнаружить не удалось, поскольку в каждом кластере максимум один ген имеет Z-DNA в промотере. Такой результат сначала меня очень удивил, и я стала искать ошибку, после чего поняла, что ее нет. Все дело в особенностях данного рода бактерий.

Обратившись обратно к гистограммам значений ZH-Score, можно заметить, что достаточно мало участков в принципе имеют высокий ZH-Score, то есть там максимум в районе 30 участков. Также по первой сводной таблице видно, что участков с ZH-score > 500 очень мало относительно общего количества.

Действительно, построив гистограммы для участков с ZH-Score < 500, можно обнаружить, что огромное количество участков не является Z-DNA (score в районе нуля). Таким образом, данный род бактерий не имеет склонности к образованию Z-DNA, и мы обнаружили достаточно мало генов, ответственных за это - в файликах пересечений Z-DNA и промотеров в среднем от 3 до 17 значений. Это привело к тому, что белок конкретного вида, находящийся в кластере, с очень низкой вероятностью является производным гена, связанного с Z-DNA. Получился достаточно интересный вывод про данный род Clostridium. Я немного расстроилась, что получился отрицательный результат (и не пришлось прибегнуть к выравниванию и доп. визуализации), однако это наука и это нормально (и на мой взгляд, даже очень интересное наблюдение), поэтому рассчитываю на то, что за это мне не снизят оценку.

Гистограммы участков Z-DNA с ZH-Score < 500:

![image](https://user-images.githubusercontent.com/60008375/173359889-1b7683ec-74c3-4159-ac98-c53e38d51f66.png)
![image](https://user-images.githubusercontent.com/60008375/173360875-0f59000c-847a-48c0-ac58-c33d1474d6e7.png)
![image](https://user-images.githubusercontent.com/60008375/173361659-96781d84-8d71-454e-af0c-4210cc2927be.png)
![image](https://user-images.githubusercontent.com/60008375/173361985-57bec49c-3d22-4230-b65a-944fca1de055.png)
![image](https://user-images.githubusercontent.com/60008375/173362247-ae81771f-0e5c-459a-ab45-327addbd67c3.png)

Итого лишь в 16 кластерах один ген из всех 5 видов имеет Z-DNA в промотере, в остальных же кластерах все белки никоим образом не связаны с образованием Z-DNA.

![image](https://user-images.githubusercontent.com/60008375/173372323-d7d82f92-2d86-41d4-9987-2beea3c580c0.png)

## Бонусная часть задания - предсказание G-квадруплексов

### Сводная таблица по геномам

|index|Название вида|Количество предсказанных участков G-квадруплексов|Общая длина участков G-квадруплексов|
|---|---|---|---|
|0|Clostridium aceticum|8|216|
|1|Clostridium botulinum A str\. ATCC 3502|0|0|
|2|Clostridium cochlearium|2|49|
|3|Clostridium novyi|0|0|
|4|Clostridium septicum|2|43|

### Гистограммы значений score для G-квадруплексов

![image](https://user-images.githubusercontent.com/60008375/173436433-46b5371d-b291-461a-aeb1-5ab5e4caf8a8.png)

![image](https://user-images.githubusercontent.com/60008375/173436460-b1b9bea4-098a-4a7d-b8f0-b7a439b0cdea.png)

![image](https://user-images.githubusercontent.com/60008375/173436491-925dc095-0a3d-428c-9efa-38acb2c782c7.png)

### Визуализация генов и предсказанных участков G-квадруплексов

**Clostridium aceticum (первый геном)**

![image](https://user-images.githubusercontent.com/60008375/173433872-7969a91e-1d62-40a3-b77d-af9aa64fd136.png)

**Clostridium cochlearium (третий геном)**

![image](https://user-images.githubusercontent.com/60008375/173434129-6bff6777-d386-44ff-ab55-1f655a27f6b0.png)

**Clostridium septicum (пятый геном)**

![image](https://user-images.githubusercontent.com/60008375/173434153-02a30968-af88-4892-a309-5189792ff6b5.png)

### Выводы
