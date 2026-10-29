# Predykcja WZW C

## 1. Opis projektu

## 2. Opis zbioru danych

### 2.1 Liczebność

**Ogólna liczba obserwacji:** 615,

**Liczba obserwacji z brakującymi wartościami:** 26,

**Liczba obserwacji rozważanych w projekcie:** 589,

**Liczba cech:** 13,

### 2.2 Cechy zbioru danych
**UWAGA!!!** Jednostki poszczególnych cech **nie pochodzą ze źródla** i są **wywnioskowane przez autora.**
Ponieważ cechy [4:15] zbioru we źródle są podane bez jednostek pomiarowych, jednostki zostały wywnioskowane
na podstawie charakterystycznych poziomów poszczególnych wskaźników przy użyciu Sztucznej Inteligencji. [[użyty prompt]](#wywnioskowanie-jednostek)

Z  [dokumentu, wprowadzającego do zbioru [1]](https://api.semanticscholar.org/CorpusID:55532259) wiadomo, że dane pochodzą z badań Wyższej Szkoły Medycznej Hannoweru,
a szczególne pomiary cech krwi wykonano na analizatorze Roche Modular P800 (Hoffmann i in., *J Lab Precis Med*, 2018).
W laboratoriach krajów Unii Europiejskiej standardem są jednostki układu SI.

| Cecha | Opis | Jednostka | Przyjmowane wartości |
|---|---|---|---|
| Category | Diagnoza pacjenta | - | 0=Blood Donor, 0s=suspect Blood Donor, 1=Hepatitis, 2=Fibrosis, 3=Cirrhosis |
| Age | Wiek pacjenta | Wiek w latach | [23, 77] |
| Sex | Płec pacjenta | - | f- kobieta, m- mężczyzna |
| ALB | Albumine | g/L | [14.9, 82.2] |
| ALP | Alkaline phosphatase | U/L | [11.3, 417] |
| ALT | Alanine Transaminase | U/L | [0.90, 325] |
| AST | Aspartate Transaminase | U/L | [10.6, 324] |
| BIL | Bilirubin | $\mu \text{mol/L}$ | [0.80, 209] |
| CHE | Acetylcholinesterase | kU/L | [1.4, 16.4] |
| CHOL | Cholesterol | mmol/L | [1.4, 9.7] |
| CREA | Creatinine | $\mu \text{mol/L}$ | [8, 1079] |
| GGT | Gamma-Glutamyl Transferase | U/L | [4.5, 651] |
| PROT | Proteins | g/L | [44.8, 86.5] |

### 2.3 Źródlo
Lichtinghagen, R., Klawonn, F., & Hoffmann, G. (2020). HCV data [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5D612.

## 5. Użyte prompty

### 5.1 Wywnioskowanie jednostek

#### 5.1.1 Narzędzie AI
Claude Sonnet 5.5, Medium Effort.

#### 5.1.2 Prompt
```
https://www.kaggle.com/datasets/fedesoriano/hepatitis-c-dataset?resource=download

In this dataset, which units are used to measure each respectful blood feature?
I'm interested in the columns from 5 to 14, which refer to laboratory data.
I'll provide you a piece of .csv file values. Then, I want you to find the unit
and explain each unit in detail for every feature.
Find any relevant data about the units of measures, methodology or used hardware
in the origin's introductory paper:
https://jlpm.amegroups.org/article/view/4401/5425

Here are some .csv values from the file, coming from the healthy patients.
Infer the units comparing the actual values from the dataset and known
characteristic values for relevant blood measures:
```

```csv
"","Category","Age","Sex","ALB","ALP","ALT","AST","BIL","CHE","CHOL","CREA","GGT","PROT"
"1","0=Blood Donor",32,"m",38.5,52.5,7.7,22.1,7.5,6.93,3.23,106,12.1,69
"2","0=Blood Donor",32,"m",38.5,70.3,18,24.7,3.9,11.17,4.8,74,15.6,76.5
"3","0=Blood Donor",32,"m",46.9,74.7,36.2,52.6,6.1,8.84,5.2,86,33.2,79.3
"4","0=Blood Donor",32,"m",43.2,52,30.6,22.6,18.9,7.33,4.74,80,33.8,75.7
"5","0=Blood Donor",32,"m",39.2,74.1,32.6,24.8,9.6,9.15,4.32,76,29.9,68.7
"6","0=Blood Donor",32,"m",41.6,43.3,18.5,19.7,12.3,9.92,6.05,111,91,74
"7","0=Blood Donor",32,"m",46.3,41.3,17.5,17.8,8.5,7.01,4.79,70,16.9,74.5
"8","0=Blood Donor",32,"m",42.2,41.9,35.8,31.1,16.1,5.82,4.6,109,21.5,67.1
"9","0=Blood Donor",32,"m",50.9,65.5,23.2,21.2,6.9,8.69,4.1,83,13.7,71.3
"10","0=Blood Donor",32,"m",42.4,86.3,20.3,20,35.2,5.46,4.45,81,15.9,69.9
"11","0=Blood Donor",32,"m",44.3,52.3,21.7,22.4,17.2,4.15,3.57,78,24.1,75.4
"12","0=Blood Donor",33,"m",46.4,68.2,10.3,20,5.7,7.36,4.3,79,18.7,68.6
"13","0=Blood Donor",33,"m",36.3,78.6,23.6,22,7,8.56,5.38,78,19.4,68.7
"14","0=Blood Donor",33,"m",39,51.7,15.9,24,6.8,6.46,3.38,65,7,70.4
"15","0=Blood Donor",33,"m",38.7,39.8,22.5,23,4.1,4.63,4.97,63,15.2,71.9
"16","0=Blood Donor",33,"m",41.8,65,33.1,38,6.6,8.83,4.43,71,24,72.7
"17","0=Blood Donor",33,"m",40.9,73,17.2,22.9,10,6.98,5.22,90,14.7,72.4
"18","0=Blood Donor",33,"m",45.2,88.3,32.4,31.2,10.1,9.78,5.51,102,48.5,76.5
"19","0=Blood Donor",33,"m",36.6,57.1,38.9,40.3,24.9,9.62,5.5,112,27.6,69.3
"20","0=Blood Donor",33,"m",42,63.1,32.6,34.9,11.2,7.01,4.05,105,19.1,68.1
"21","0=Blood Donor",33,"m",44.3,49.8,32.1,21.6,13.1,7.44,5.59,103,30.2,74
"22","0=Blood Donor",33,"m",46.7,88.3,23.4,23.9,7.8,9.42,4.62,78,29.5,74.3
"23","0=Blood Donor",34,"m",42.7,65.3,46.7,30.3,23.4,10.95,5.06,75,99.6,69.1
"24","0=Blood Donor",34,"m",43.4,46.1,97.8,46.2,11.3,7.99,3.62,71,35.3,69.6
"25","0=Blood Donor",34,"m",40.5,32.4,29.6,27.1,5.8,10.5,4.56,91,26.6,72
"26","0=Blood Donor",34,"m",44.8,77.7,36.9,31,19.5,10.51,5.59,80,23.7,78.9
"27","0=Blood Donor",34,"m",42.6,27,21.4,21.7,7.2,8.15,6.79,85,13.9,67.7
"28","0=Blood Donor",34,"m",29,41.6,29.1,16.1,4.8,6.82,4.03,62,14.5,53.2
"29","0=Blood Donor",34,"m",44.6,84.1,19.6,29.8,5.8,7.6,5.07,95,9.9,71.9
"30","0=Blood Donor",34,"m",46.8,61.7,24.5,24.2,23.1,10.99,4.6,83,23.8,73.1
"31","0=Blood Donor",34,"m",41.8,75.8,30.9,35.5,6.1,9.97,5.94,89,48.5,71.3
"32","0=Blood Donor",34,"m",46.1,70.6,35.8,30,7.6,7.7,4.2,93,14.3,78.7
"33","0=Blood Donor",34,"m",43.6,58.9,47.1,31.1,18.5,9.14,4.99,95,22.2,69.3
"34","0=Blood Donor",35,"m",37.5,69.8,37.1,25,7.8,11.66,5.73,84,27.3,71
"35","0=Blood Donor",35,"m",42.1,68.3,37.2,56.2,11.1,9.3,4.63,99,16.8,73.6
"36","0=Blood Donor",35,"m",44.7,79.3,53.5,30.8,9.7,11.39,7.04,88,77.3,77.1
"37","0=Blood Donor",35,"m",41.5,115.1,24.1,30.4,5.7,9.41,4.33,81,22.2,71.3
"38","0=Blood Donor",35,"m",48.7,72.7,24.1,31,45.1,9.4,3.8,90,20,75.8
"39","0=Blood Donor",35,"m",47.3,92.2,30.7,25.7,6.6,11.58,5.9,82,36.9,77.8
"40","0=Blood Donor",35,"m",44.5,70.3,26.2,25.1,5.1,10.12,4.69,82,20.7,67.2
"41","0=Blood Donor",35,"m",47.4,54.5,18.6,21.6,10.3,8.1,6.23,66,28.1,74
"42","0=Blood Donor",35,"m",51,82.7,29.3,26.8,8.7,12.32,5.44,89,25,77.3
"43","0=Blood Donor",35,"m",27.8,99,30.7,27.8,9.4,6.8,4.27,65,40.5,80.7
"44","0=Blood Donor",36,"m",46.1,58.5,26.8,25.3,6,6.61,5.07,71,10.5,79.6
"45","0=Blood Donor",36,"m",45.5,57.6,22.5,19.5,7.5,5.28,4.06,88,62.5,71.6
"46","0=Blood Donor",36,"m",41.7,77.2,103.6,46.9,10.4,12.21,5.63,88,20.9,69.3
"47","0=Blood Donor",36,"m",45.9,58.8,29.7,27.7,11.7,5.6,4.89,93,23.1,70.8
"48","0=Blood Donor",36,"m",48.7,65,11.5,18,7.4,8.02,7.35,69,14.2,73.4
"49","0=Blood Donor",36,"m",53,66.4,40.8,23.2,7.5,8.73,5.81,75,36.1,77.3
"50","0=Blood Donor",36,"m",47.8,89,48.5,38.4,8.6,8.26,5.62,96,21.9,76.2
"51","0=Blood Donor",36,"m",42.6,65.3,35.8,27.1,15.7,10.66,4.38,96,34.7,71
"52","0=Blood Donor",36,"m",42.4,47.3,23,25.5,6.1,9.46,5.29,79,17.5,73.8
"53","0=Blood Donor",36,"m",48.9,82.8,16.9,24.4,8.9,8.91,5.1,97,14.8,79.9
"54","0=Blood Donor",37,"m",31.4,106,16.6,17,2.4,5.95,5.3,68,22.9,72.3
"55","0=Blood Donor",37,"m",42.9,70.7,16.3,24.1,15.7,9.03,6.8,93,70.1,73.4
"56","0=Blood Donor",37,"m",44,57.4,26.1,24.6,9.7,10.41,6.17,83,38.9,76.5
"57","0=Blood Donor",37,"m",41.5,64.6,23.7,29.9,9.3,5.49,3.97,100,10.4,69.3
"58","0=Blood Donor",37,"m",47.9,68.8,40.3,46.9,6,9.76,6.42,81,22.7,80.6
"59","0=Blood Donor",37,"m",44.8,94.3,32.2,36.7,6.3,9.76,4.12,113,23.8,72.5
"60","0=Blood Donor",37,"m",38.6,61.2,24.6,31.9,7.9,6.02,4.63,72,10.3,56.3
"61","0=Blood Donor",37,"m",51.2,84.5,18.8,24.7,9.9,8.62,6.59,94,25.3,76.3
"62","0=Blood Donor",37,"m",41.9,77.5,24.9,25.8,4.1,8.7,4.36,84,16,71.5
"63","0=Blood Donor",37,"m",46.1,44.3,42.7,26.5,6.4,10.86,5.05,74,22.2,73.1
"64","0=Blood Donor",37,"m",50.4,48.5,19.4,27.5,11.6,5.78,4.93,90,27.8,75
"65","0=Blood Donor",37,"m",33.9,64,91.7,44.7,9.1,8.35,5.4,95,30.3,74.7
"66","0=Blood Donor",37,"m",42.9,61.8,96.1,44.1,9.6,7.82,5.1,82,32.3,69.3
"67","0=Blood Donor",37,"m",40.8,118.9,17.2,19.2,3.2,9.17,4.26,88,13.5,72
"68","0=Blood Donor",37,"m",43.6,72.8,51.4,43.7,13.8,8.16,4.88,70,94.5,75.2
"69","0=Blood Donor",37,"m",46.4,53.3,20.2,24.9,8.7,8.63,5.9,86,23.3,78.9
"70","0=Blood Donor",37,"m",48.7,62.3,21,21.1,41.9,9.71,4.02,84,16,75.1
"71","0=Blood Donor",38,"m",48.1,63.2,11.7,14.7,5.1,8.83,3.87,85,9.5,73.1
"72","0=Blood Donor",38,"m",39.9,62.9,71.7,43.9,10.4,10.9,7.01,99,88.3,73.1
"73","0=Blood Donor",38,"m",45.5,50.2,16.3,22.8,10.9,8.73,5.88,103,13.8,76.1
"74","0=Blood Donor",38,"m",43.4,58.9,45.7,45.7,9.2,10.86,5.74,90,30,73.9
"75","0=Blood Donor",38,"m",41.2,43.8,19.9,20.5,10.1,5.95,3.91,63,70.8,67.4
"76","0=Blood Donor",38,"m",44.7,69.4,47.4,35.1,16.7,6.9,4.14,67,17.3,70.1
"77","0=Blood Donor",38,"m",42,42.7,34.8,42.2,3.3,6.1,4.74,96,14.6,66.7
"78","0=Blood Donor",38,"m",48.4,44.9,23.4,22.1,7.9,10.53,7.51,87,43.2,82.6
"79","0=Blood Donor",38,"m",38.3,81.5,65.9,35.3,14,11,5.46,80,45.2,68.1
"80","0=Blood Donor",38,"m",40.5,61.7,18.6,24.7,6.7,8.47,6.05,89,19.6,75.6
"81","0=Blood Donor",39,"m",45.1,63.9,26,21.3,9.3,8.57,5.24,79,29.4,71.2
"82","0=Blood Donor",39,"m",38.8,52.5,54.3,31.3,10.1,10.68,6.26,81,31.5,77.2
"83","0=Blood Donor",39,"m",47,66.5,24.8,29.1,10.5,10.04,6.26,73,49.8,78.4
"84","0=Blood Donor",39,"m",36.6,71.3,28.9,25.9,6.1,5.7,4.66,77,22.6,66.3
"85","0=Blood Donor",39,"m",43.9,90.1,87.9,60.6,8.6,9.94,4.64,98,99.3,66.2
"86","0=Blood Donor",39,"m",43.4,48.6,33.4,35,23.4,9.68,5.55,73,22.1,75.2
"87","0=Blood Donor",39,"m",36,36.5,21.5,25.7,3.3,8.43,4.85,93,23.1,70.5
"88","0=Blood Donor",39,"m",45.7,73.4,45.5,33.8,5,9.07,4.41,82,20.6,78.9
"89","0=Blood Donor",39,"m",37.5,80.2,32.6,25.3,2.7,9.3,6.85,72,27.5,73.1
"90","0=Blood Donor",39,"m",46.4,102.9,44.4,26.2,4.1,9.29,8.89,103,64,72.2
"91","0=Blood Donor",39,"m",45.8,62.5,20.7,22.8,45.5,8.61,4.78,77,15.9,75.5
"92","0=Blood Donor",39,"m",46.1,77.1,34.9,37.6,4.1,13.86,8.11,94,76.9,71.1
"93","0=Blood Donor",40,"m",47.8,68,17.5,22.3,7.7,9.94,6.09,88,23.3,73.9
"94","0=Blood Donor",40,"m",44.5,45.7,25.9,27.6,9.2,8.93,4.49,87,17,71.2
"95","0=Blood Donor",40,"m",41.4,67.5,59.8,36.8,7.3,4.18,6.02,76,92.7,72.5
"96","0=Blood Donor",40,"m",45,74.2,20.9,29.1,12,9.1,6.29,92,24.1,74.1
"97","0=Blood Donor",40,"m",39.1,66.5,33.3,32.9,14.8,7.87,4.91,88,18.5,68.8
"98","0=Blood Donor",40,"m",45.1,63.4,39.6,31.4,19.7,11.31,4.74,91,18.2,81.1
"99","0=Blood Donor",40,"m",45.4,52.9,41.3,26.2,10.6,10.27,6.85,82,40.2,76.6
"100","0=Blood Donor",40,"m",46.9,61.8,27.4,43,7,7.26,5.09,98,14.2,75.3
```


## 6. Odnośniki
[1] Hoffmann, G.F., Bietenbeck, A., Lichtinghagen, R., & Klawonn, F. (2018). Using machine learning techniques to generate laboratory diagnostic pathways—a case study. Journal of Laboratory and Precision Medicine.
https://api.semanticscholar.org/CorpusID:55532259
