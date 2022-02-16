# hse_hw1_meth
Ссылка на Colab: https://colab.research.google.com/drive/1uqVNKH4LDPMrtg8a999OFBKnwbYrgONO?usp=sharing

Colab анализ QC прочтений: 
# Анализ QC прочтений
Образец SRR5836473_2 (8 cell)

### a) Число ридов

![table](https://user-images.githubusercontent.com/93256219/154359013-16e86292-9f7e-466f-94f3-6beb5f2a71ff.png)

### b) BASH-скрипт
```
!ls *pe.bam | xargs -P 4 -tI{} deduplicate_bismark  --bam  --paired  -o s_{} {}
```
### Процент дуплицированных прочтений

![table2](https://user-images.githubusercontent.com/93256219/154360977-34268c6a-1dff-48cd-b1be-bcc5e8f316fb.png)

### d) M-Bias Plot
Описание

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

