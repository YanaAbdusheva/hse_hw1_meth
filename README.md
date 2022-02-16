# hse_hw1_meth
Ссылка на Colab: https://colab.research.google.com/drive/1uqVNKH4LDPMrtg8a999OFBKnwbYrgONO?usp=sharing
Colab анализ QC прочтений: 
# Анализ QC прочтений
Образец SRR3824222_1 (Epiblast)

### a) Число ридов

![table](https://user-images.githubusercontent.com/93256219/154359013-16e86292-9f7e-466f-94f3-6beb5f2a71ff.png)

### b) BASH-скрипт
```
!ls *pe.bam | xargs -P 4 -tI{} deduplicate_bismark  --bam  --paired  -o s_{} {}
```
# Процент дуплицированных прочтений

![table2](https://user-images.githubusercontent.com/93256219/154360977-34268c6a-1dff-48cd-b1be-bcc5e8f316fb.png)

### d) M-Bias Plot
Мы видим график смещения метилирования, который показывает пропорцию метилирования для каждой возможной позиции в прочтении. На графиках также показано абсолютное значение  метиловых calls (и метилированных, и не метилированных). В нашем случае, мы имеем дело с paired-end записью, поэтому у нас два разных графика M-bias. На данных графиках мы можем выявить смещение 3'-end-repair начальных значений в двух прочтениях paired-end reads. 

## SRR5836473

![1](https://user-images.githubusercontent.com/93256219/154363988-1d2d27d7-db83-4901-a23e-c1063c0a47aa.png)
![2](https://user-images.githubusercontent.com/93256219/154363993-1d5b9a04-a447-475f-8afc-9766fdd82ece.png)
