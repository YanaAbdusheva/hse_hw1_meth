# hse_hw1_meth
Ссылка на Colab: https://colab.research.google.com/drive/1uqVNKH4LDPMrtg8a999OFBKnwbYrgONO?usp=sharing
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
