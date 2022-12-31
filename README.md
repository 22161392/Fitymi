# Fitymi (Fake it till you make it)
Fitymi is bedoelt om een fake dataset te generenen in Python om deze vervolgens te kunnen gebruiken met Matplotlib en PowerBI.
Hiervoor wordt o.a. gebruik gemaakt van de volgende modules:

1. faker
2. pandas
3. matplotlib
4. openpyxl


Als eerste wordt er een python list gemaakt met faker. Voorbeeld van een lijst gemaakt met faker:
```
[['Casper', 'van Spreeuwel', datetime.date(1921, 12, 24), '(0777) 687432', 'Clinical cytogeneticist', 'Ouwel & Kronenberg', 'sophiavan-grinsven@anwb.com', '185497068', 'NL46WQKS8072829989', '573', 'Lisalaan', '5367HQ', 'Tiendeveen', 'Drenthe', 'Sirin Labs', '€84.449,72', '2001', ('52.09', '5.23333')],
['Dana', 'Willemsen', datetime.date(2004, 4, 10), '+31341-133602', 'Pension scheme manager', 'Ten Brinke Groep', 'nspies@kok.net', '427986151', 'NL03SDZZ8980172390', '3', 'Quintensteeg', '6208 RW', 'Vrouwenparochie', 'Drenthe', 'PotCoin', '€8,88', '2010', ('52.31333', '6.92917')], 
['Tess', 'der Kijnder', datetime.date(1964, 6, 11), '+3151-7379963', 'Therapist, horticultural', 'Fugro', 'van-velthovensaar@martens.com', '482735697', 'NL83LAOO3867176726', '60', 'Mirthepad', '4858 CP', 'Hindeloopen', 'Limburg', 'AMP', '€556,87', '1986', ('52.71083', '5.74861')], 
['Aylin', 'Emmen', datetime.date(1984, 1, 1), '+31(0)124-415544', 'Armed forces logistics/support/administrative officer', 'Unilever', 'tessvan-salm@stichting.net', '624837099', 'NL44ECIZ1957332586', '37', 'Mirthebaan', '4488PD', 'Bontebok', 'Friesland', 'Dogecoin', '€98.985,47', '1992', ('51.955', '5.22778')], 
['Milo', 'Bleijenberg', datetime.date(2022, 11, 5), '(037) 4356874', 'Field trials officer', 'Boels', 'mullerloes@gmail.com', '632459189', 'NL87CGMV8980258984', '015', 'Juliehof', '4140EE', 'Tienray', 'Gelderland', 'DigitalNote', '€43,12', '2019', ('51.95838', '4.47124')]]
```

Deze wordt dan omgezet naar een pandas dataframe.
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
Verschillen datatype worden aangepast in dit dataframe zodat deze beter werken in Matplotlib en PowerBI:
| Voor | Na |
|--|--|
|![image](https://user-images.githubusercontent.com/113904065/210148952-fdf793d4-432e-48c9-b1b3-b6dc13310bcc.jpeg)|![image](https://user-images.githubusercontent.com/113904065/210148970-9f130ed7-d6a4-4af8-a5d4-174ae6a75331.jpeg)|
