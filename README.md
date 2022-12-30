# Hoe gerbruik je Fitymi (Fake it till you make it)
Fitymi is bedoelt om een fake dataset te generenen in Python.

```
def manipuleer_klant_data(klanten_lijst, bestand):
    #klanten_lijst=genereer_klant_data(land='nl_NL', aantal=1000)
    csv_kolommen = ['KlantId', 'Voornaam', 'Achternaam', 'Geboortedatum','Telefoonnummer','Beroep','Bedrijf','EMail','BSNNummer','IBAN','Huisnummer','Straatnaam','Postcode','Woonplaats','Provincie','CryptoNaam', 'Bedrag', 'AankoopJaar', 'Geo']
    df = pd.DataFrame(klanten_lijst,columns=csv_kolommen)
    df['Bedrag'] = df['Bedrag'].str.replace('€','', regex=False)
    df['Bedrag'] = df['Bedrag'].str.replace('.','', regex=False)
    df['Bedrag'] = df['Bedrag'].str.replace(',','.', regex=False)
    df["Geboortedatum"] = pd.to_datetime(df["Geboortedatum"])

    def split_coordinates(coordinates):
        latitude, longitude = coordinates
        return pd.Series([longitude, latitude])

    df[['Longitude', 'Latitude']] = df['Geo'].apply(split_coordinates)

    df = df.drop(columns=['Geo'])

    df[['KlantId','BSNNummer', 'Huisnummer','Bedrag','AankoopJaar', 'Longitude', 'Latitude']] = df[['KlantId','BSNNummer', 'Huisnummer','Bedrag','AankoopJaar', 'Longitude', 'Latitude']].apply(pd.to_numeric)

    try:
        df.to_excel(bestand, sheet_name='BitMoney', index=False)
    except FileNotFoundError:
        print(f' Kan het bestand: {bestand} niet aanmaken.')

    df.info()
    return df
```
![image](https://user-images.githubusercontent.com/113904065/210086124-e976ec61-49e0-4411-bb57-d3afd8447295.jpeg)

| Voor | Na |
|--|--|
|![image](https://user-images.githubusercontent.com/113904065/210085131-5d69b3b2-49c5-45ca-b062-4cabb67803c0.jpeg)|![image](https://user-images.githubusercontent.com/113904065/210085197-75510411-e83f-4973-9a08-e77e91c34f31.jpeg)|
