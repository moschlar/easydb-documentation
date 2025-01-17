---
menu:
  main:
    name: "5.89 (Anfang September 2021)"
    identifier: "5.89"
    parent: "releases"
    weight: -589
---

> Für das Release 5.89.0 ist ein **Re-Index nötig**, bitte planen Sie entsprechende Zeit für das Einspielen des Updates ein. 

# Version 5.89.2

*Veröffentlicht am 20.09.2021*

## Webfrontend

### Behoben

* Powerpoint-Export: Das Aufrufen des Exporters ist jetzt wieder möglich.
* Mappen: Freigabelinks haben in einigen Fällen nicht korrekt funktioniert.

## Server

### Neu

* **Pool-Management**: Der Rechtecheck für Mappen kann von Nutzern mit dem `system.root`-Recht nach Bestätigung übersprungen werden.

# Version 5.89.1

*Veröffentlicht am 10.09.2021*

## Webfrontend

### Behoben

* **Neue Objekte**: In einigen Fällen wurde der Dialog nicht korrekt geöffnet und es kam zu einem Javascript-Fehler.

# Version 5.89.0

*Veröffentlicht am 08.09.2021*

## Webfrontend

### Verbessert

* **CSV-Importer**: Update-Support für Nummernfelder wurde hinzugefügt.
* **Metadaten**: _Fester Wert_ kann jetzt angepasst werden.
* **Maskenmanagement**: Mehr Sortierfelder für Mehrfachfelder in **FYLR** (easydb 6).

### Behoben

* **Mappen**: Verbesserte Fehlerbehandlung bei verlinkten Objekttypen mit Assetfeldern.

* **Detail / Editor**: Korrekturen für Pfade beim Format _Kurz_ von verlinkten Objekten.

* **Suche**: Anzeigeproblem bei Reversere verschachtelten Objekten in der Tabellenansicht behoben.

* **Editor**: Kleinere Fixes bei der textuellen Erkennung von Datierungen.

## Server

### Verbessert

* **/api/user**: Mehr Felder für Nutzer durchsuchbar.
* **Suggest-Index** Aufbau ist 20-30% schneller.
* **Plugins**: Die Konfigurationsdateien für Plugins wurde alle in `manifest.yml`umbenannt.

### Behoben

* **/api/collection**: `create_object` wird aktualisiert, wenn entsprechende Basistypen betroffen sind.
* **/api/user**: Verbesserte Fehlermeldung bei falscher Version.

# Prüfsummen

Hier die Prüfsummen unserer Docker-Images (neueste Version): 

```ini
docker.easydb.de/pf/chrome               sha256:b5fe29ee03c23bea847c4333ad8d675ed333d51834ce8ee5855072e213a4a5c8
docker.easydb.de/pf/eas                  sha256:1031f6e7459e430a3233d38f5a3678562fde6bf2e578672838b4128a1eb258d1
docker.easydb.de/pf/elasticsearch        sha256:2a9ca9620e35567d8ea6c666055e4377ca556d16b0a619f2198d9cc9fe9bc526
docker.easydb.de/pf/fylr                 sha256:a8e34a88bb2604f5f4cfc58776854f7cc2b07979c55171d017eabc54821a9652
docker.easydb.de/pf/postgresql-11        sha256:b5cd1da4a100450e07b3f6111a4842b1741b018465c6923e62ab636a705c2b93
docker.easydb.de/pf/server-base          sha256:e341f0e9857e1ea18b349037f55807691b955133b17f70888ca4dbf4a2c85d20
docker.easydb.de/pf/webfrontend          sha256:53d135e2aa1f159d3d0c53e7982f0870448e8dd437f71d2fe0019a23a9e0dc12
```

