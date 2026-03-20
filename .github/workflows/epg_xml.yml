name: XML EPG Grabber

on:
  workflow_dispatch:
  schedule:
    - cron: '0 4 * * *'

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Pobranie repozytorium
        uses: actions/checkout@v4
        
      - name: Konfiguracja Python 3.10
        uses: actions/setup-python@v4
        with:
          python-version: '3.10'
          
      - name: Instalacja bibliotek
        run: pip install requests beautifulsoup4 lxml
        
      - name: Uruchomienie skryptu EPG
        # Zmień "test_onet_05.py" na taką nazwę, jaką nadasz plikowi na GitHubie
        run: python test_onet_05.py 
        
      - name: Zapis i wysyłka pliku na GitHuba
        run: |
          git config --global user.name "EPG-Bot"
          git config --global user.email "bot@epg.com"
          git add Output/onet_test_full.xml
          git commit -m "Codzienna aktualizacja EPG XML" || echo "Brak zmian do zapisu"
          git push
