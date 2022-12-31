# Fitymi (Fake it till you make it)
Fitymi is bedoelt om een fake dataset te genereren in Python om deze vervolgens te kunnen gebruiken met Matplotlib en PowerBI.
Hiervoor wordt o.a. gebruik gemaakt van de volgende modules:

1. faker
2. pandas
3. matplotlib
4. openpyxl

Fitymi wordt via een menu aangestuurd:
![image](https://user-images.githubusercontent.com/113904065/210151727-31a92e18-3d71-43de-b3b2-306481c6ad1b.jpeg)

### 1. Maak een dataset en schrijf deze weg als een xlsx bestand

Als eerste wordt er een python list gemaakt met faker. Voorbeeld van een lijst gemaakt met faker:
```
[['Casper', 'van Spreeuwel', datetime.date(1921, 12, 24), '(0777) 687432', 'Clinical cytogeneticist', 'Ouwel & Kronenberg', 'sophiavan-grinsven@anwb.com', '185497068', 'NL46WQKS8072829989', '573', 'Lisalaan', '5367HQ', 'Tiendeveen', 'Drenthe', 'Sirin Labs', '€84.449,72', '2001', ('52.09', '5.23333')],
['Dana', 'Willemsen', datetime.date(2004, 4, 10), '+31341-133602', 'Pension scheme manager', 'Ten Brinke Groep', 'nspies@kok.net', '427986151', 'NL03SDZZ8980172390', '3', 'Quintensteeg', '6208 RW', 'Vrouwenparochie', 'Drenthe', 'PotCoin', '€8,88', '2010', ('52.31333', '6.92917')], 
['Tess', 'der Kijnder', datetime.date(1964, 6, 11), '+3151-7379963', 'Therapist, horticultural', 'Fugro', 'van-velthovensaar@martens.com', '482735697', 'NL83LAOO3867176726', '60', 'Mirthepad', '4858 CP', 'Hindeloopen', 'Limburg', 'AMP', '€556,87', '1986', ('52.71083', '5.74861')], 
['Aylin', 'Emmen', datetime.date(1984, 1, 1), '+31(0)124-415544', 'Armed forces logistics/support/administrative officer', 'Unilever', 'tessvan-salm@stichting.net', '624837099', 'NL44ECIZ1957332586', '37', 'Mirthebaan', '4488PD', 'Bontebok', 'Friesland', 'Dogecoin', '€98.985,47', '1992', ('51.955', '5.22778')], 
['Milo', 'Bleijenberg', datetime.date(2022, 11, 5), '(037) 4356874', 'Field trials officer', 'Boels', 'mullerloes@gmail.com', '632459189', 'NL87CGMV8980258984', '015', 'Juliehof', '4140EE', 'Tienray', 'Gelderland', 'DigitalNote', '€43,12', '2019', ('51.95838', '4.47124')]]
```

Deze wordt dan omgezet naar een pandas dataframe:
```
  Voornaam     Achternaam Geboortedatum    Telefoonnummer  \
0   Casper  van Spreeuwel    1921-12-24     (0777) 687432   
1     Dana      Willemsen    2004-04-10     +31341-133602   
2     Tess    der Kijnder    1964-06-11     +3151-7379963   
3    Aylin          Emmen    1984-01-01  +31(0)124-415544   
4     Milo    Bleijenberg    2022-11-05     (037) 4356874   

                                              Beroep             Bedrijf  \
0                            Clinical cytogeneticist  Ouwel & Kronenberg   
1                             Pension scheme manager    Ten Brinke Groep   
2                           Therapist, horticultural               Fugro   
3  Armed forces logistics/support/administrative ...            Unilever   
4                               Field trials officer               Boels   

                           EMail  BSNNummer                IBAN  Huisnummer  \
0    sophiavan-grinsven@anwb.com  185497068  NL46WQKS8072829989         573   
1                 nspies@kok.net  427986151  NL03SDZZ8980172390           3   
2  van-velthovensaar@martens.com  482735697  NL83LAOO3867176726          60   
3     tessvan-salm@stichting.net  624837099  NL44ECIZ1957332586          37   
4           mullerloes@gmail.com  632459189  NL87CGMV8980258984          15   

     Straatnaam Postcode       Woonplaats   Provincie   CryptoNaam  \
0      Lisalaan   5367HQ       Tiendeveen     Drenthe   Sirin Labs   
1  Quintensteeg  6208 RW  Vrouwenparochie     Drenthe      PotCoin   
2     Mirthepad  4858 CP      Hindeloopen     Limburg          AMP   
3    Mirthebaan   4488PD         Bontebok   Friesland     Dogecoin   
4      Juliehof   4140EE          Tienray  Gelderland  DigitalNote   

   AankoopBedrag  AankoopJaar  Longitude  Latitude  
0       84449.72         2001    5.23333  52.09000  
1           8.88         2010    6.92917  52.31333  
2         556.87         1986    5.74861  52.71083  
3       98985.47         1992    5.22778  51.95500  
4          43.12         2019    4.47124  51.95838
```
Verschillen datatype worden aangepast in dit dataframe zodat deze beter werken in Matplotlib/ PowerBI en wordt Geo(17) gesplits in Longitude(17) en Laditude(18):
| Voor | Na |
|--|--|
|![image](https://user-images.githubusercontent.com/113904065/210148952-fdf793d4-432e-48c9-b1b3-b6dc13310bcc.jpeg)|![image](https://user-images.githubusercontent.com/113904065/210148970-9f130ed7-d6a4-4af8-a5d4-174ae6a75331.jpeg)|

### 2. Open de dataset in Excel en start PowerBI online
Pandas schijft deze weg als xlsx bestand en wordt automatisch geopend:
![image](https://user-images.githubusercontent.com/113904065/210149486-a3fc8c1c-19ea-4068-a5ad-20008a478850.jpeg)

Als je kies om PowerBI online te starten, log dan in met je HHS account. Je komt dan gelijk uit bij de file import:
![image](https://user-images.githubusercontent.com/113904065/210151704-967b1884-84ea-4b88-8e49-bade8d85d34d.jpeg)

### 3. Visualiseer de dataset met matplotlib
Fitymi kan over de meeste kolommen een top x visualiseren in zowel een barh (horizontale bar grafiek) en een pie grafiek.

| Aantal en kolom | Type en voorbeeld |
|--|--|
|Stap 1: ![image](https://user-images.githubusercontent.com/113904065/210151933-8f08b6c7-892a-4d81-ae3c-e66e112fae94.jpeg)|stap 2: ![image](https://user-images.githubusercontent.com/113904065/210151981-d9c9cc56-952a-4130-bbb0-81e61ea24001.jpeg)|
|stap 3: ![image](https://user-images.githubusercontent.com/113904065/210151988-54b08b1a-c3dd-45ee-92f8-ff36c38b0c0f.jpeg)|Voorbeeld: ![image](https://user-images.githubusercontent.com/113904065/210152033-941b3ead-b36f-41a1-bcfe-175f214c4cd2.jpeg)|





