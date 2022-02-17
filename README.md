# hse_hw1_meth
Ссылка на Colab: https://colab.research.google.com/drive/1uqVNKH4LDPMrtg8a999OFBKnwbYrgONO?usp=sharing

Colab анализ QC прочтений: https://colab.research.google.com/drive/1ehPKr-moI7BkhQbpWtDn7uVhSA-eWGjU?usp=sharing
# Анализ QC прочтений
Образец SRR5836473_2 (8 cell)

Per base sequence content: по сравнению с РНК наблюдается снижение содержания гуанина, увеличение содержания аденина. Содержание тимина и цитозина почти одинаковое у метилирования. Для метилирования на протяжении всего секвенирования количество нуклеотидов разное, а в РНК наблюдается сильные флуктуации в начале, но постепенно (уже на середине) количество становится одинаковым для всех нуклеотидов.

Per sequence GC content: по сравнению с РНК наблюдается сильное отклонение от теоретического графика. Преобладающее количество GC-нуклеотидов, что соотносится с данными по уровню метилирования на стадии 8 клеток (метилирование увеличивается).

![photo](https://user-images.githubusercontent.com/93256219/154565434-4297607e-e89e-413f-abf0-bfca2efcf69a.png)
![photo2](https://user-images.githubusercontent.com/93256219/154565437-288a6d15-ba75-4f5e-8a37-731f8474420e.png)
![GC](https://user-images.githubusercontent.com/93256219/154565439-2c75d41f-98ce-456f-a709-dd6f8e1d0430.png)


### a) Число ридов
Образец | 11347700-11367700 | 40185800-40195800 
--- | --- | --- 
8cell | 1090 | 464 
epiblast | 2328 | 1062 
ICM | 1456 | 630 

### b) Bash-скрипт
```
!ls *pe.bam | xargs -P 4 -tI{} deduplicate_bismark  --bam  --paired  -o s_{} {}
```
### Процент дуплицированных прочтений
Образец | Процент
--- | --- 
8cell | 81.69
epiblast | 97.08
ICM | 90.92 

### d) M-Bias Plot
На графиках показан % метилирования в различных образцах. Самый высокий процент метилирования для Epiblast (примерно 75-78%), средний для 8Cell (примерно 45%), самый низкий - ICM (примерно 25%) 

## SRR5836473

![1](https://user-images.githubusercontent.com/93256219/154363988-1d2d27d7-db83-4901-a23e-c1063c0a47aa.png)
![2](https://user-images.githubusercontent.com/93256219/154363993-1d5b9a04-a447-475f-8afc-9766fdd82ece.png)

## SRR3824222

![3](https://user-images.githubusercontent.com/93256219/154364530-78b71064-c315-403f-979e-fe2febd50c7a.png)
![4](https://user-images.githubusercontent.com/93256219/154364534-0ea3f28c-7479-44f3-b659-3075522b1c36.png)

## SRR5836475

![5](https://user-images.githubusercontent.com/93256219/154364651-2e8e2ce4-744d-47d6-bd9d-17b49a584141.png)
![6](https://user-images.githubusercontent.com/93256219/154364652-17a27a28-2db3-41d4-b63f-c6abac5340b6.png)

### e) Гистограмма распределения метилирования цитозинов по хромосоме
Делаю выводы

![8cell](https://user-images.githubusercontent.com/93256219/154366250-b2c36b0f-a3f6-421a-9dee-9deab3ad2016.png)
![epiblast](https://user-images.githubusercontent.com/93256219/154366257-2c3b13ad-dc01-4d01-b1e2-9f4b660d7a61.png)
![icm](https://user-images.githubusercontent.com/93256219/154366258-88d1bc73-abe4-4f09-8e3f-a42803a126bd.png)

### Код
```
import pandas as pd
from matplotlib import pyplot as plt
path = 'SRR5836473_1_bismark_bt2_pe.deduplicated.bedGraph'
graph = pd.read_csv(path,  delimiter='\t', skiprows=1, header=None)
plt.figure(figsize=(10, 5))
plt.title('Распределение метилирования 8cell', fontsize=16) 
plt.hist(graph[3], bins=100, density=True)
plt.xlabel('Процент метилированных цитозинов')
plt.ylabel('Частота')
plt.show()
```
### f) pyGenomeTracks
Уровень метилирования:

![image_methyl](https://user-images.githubusercontent.com/93256219/154367500-1ebee4f9-c432-4c7f-b582-7659ef59cf80.png)

Уровень покрытия:

![image_cov](https://user-images.githubusercontent.com/93256219/154367526-70f7bb5c-47cc-4547-a322-158d58efe531.png)

