# Keuze: ophalen en beheren autorisatiegroepen
## Optie 1: Keycloak
- Groepen beheren in Keycloak
- Gebruikers koppelen aan groepen in Keycloak
- Raadplegen groepen vanuit `ODPC` (via API van Keycloak)
- Koppelen groepen aan thema's / informatiecategorieen etc in `OPDC`
- Keycloak geeft het groeplidmaatschap mee met de informatie over de ingelogde gebruiker

*Voordeel*: enkele registratie voor groepen. Het koppelen van gebruikers gebeurt op dezelfde plek als het aanmaken van groepen.

*Nadeel*: harde koppeling met Keycloak. Gemeente heeft Keycloak nodig om van de ODPC gebruik te maken

*Nadeel*: Keycloak zal een koppelvlak zijn met bijvoorbeeld Azure Entra Id. Voordat gebruikers lang Keycloak komen (omdat ze willen inloggen in de `ODRC`), zijn ze niet bekend in Keycloak en kunnen ze niet aan groepen gekoppeld worden

## Optie 2: ODRC danwel ODPC
- Groepen beheren in `ODRC` danwel `ODPC`
- Dezelfde groepen aanmaken in de Identity Provider (bijvoorbeeld Azure Entra ID, Keycloak, gemeente specifiek) 
- Gebruikers koppelen aan groepen in Identity Provider
- Raadplegen vanuit `ODPC` (via API van `ODRC` danwel uit de eigen database)
- Koppelen groepen aan thema's / informatiecategorieen etc in `OPDC`
- De Identity Provider geeft het groeplidmaatschap mee met de informatie over de ingelogde gebruiker
- Optioneel: push vanuit groepen in `ODRC` naar groepen in Identity Provider
  - Dit zou per Identity Provider geimplementeerd moeten worden

*Voordeel*: geen harde koppeling Keycloak, je mag zelf bepalen waar je de koppeling legt tussen gebruikers en groepen

*Voordeel*: als je ervoor kiest om deze groepen direct vast te leggen bij de bron waar je gebruikers vastlegt, kan je gebruikers bij voorbaat aan groepen koppelen en hoeven deze niet eerst langs Keycloak

*Nadeel*: het beheer van autorisatiegroepen gebeurt op twee plekken: `ODRC` en de Identity Provider. Deze twee moeten met elkaar up to date gehouden worden.

*Afweging tussen `ODRC` en `ODPC`*: `ODRC` is al de plek om andere lijsten bij te houden (organisaties, thema's, etc.).

*Afweging tussen `ODRC` en `ODPC`*: `ODPC` bevat een autorisatiebeheer interface. Autorisatiegroepen zijn alleen nodig binnen `ODPC`.
