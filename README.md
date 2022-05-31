# crawling
!pip install beautifulsoup4
!pip install requests


import requests
import bs4

URL = 'https://www.premierleague.com/tables'
raw = requests.get(URL)

html = bs4.BeautifulSoup(raw.text, 'html.parser')

target = html.find('div', {'class':'allTablesContainer'})
print("[ 프리미어리그 구단 순위 ]")
Clubs = target.find_all("span", {'class':'long'})
for Club in Clubs:
    print(Club.text)
