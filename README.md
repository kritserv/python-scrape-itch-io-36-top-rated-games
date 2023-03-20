# Scrape Data From itch.io 36 top rated games

A python code for scraping title author text rating genre from top 36 rated games on itch.io

# Python code

import Library
```python
from bs4 import BeautifulSoup
from requests import get
```
Load html
```python
r = get('https://itch.io/games/top-rated')
html = BeautifulSoup(r.content, 'html.parser')
```
Get elements and print result
```python
game_cells = html.find_all('div', class_ = 'game_cell')

i = 0
for cell in game_cells:

  i += 1

  title = cell.find('div', class_ = 'game_title').text.strip()
  author = cell.find('div', class_ = 'game_author').text.strip()
  text = cell.find('div', class_ = 'game_text').text.strip()
  rating_container = cell.find('div', class_='game_rating')
  rating = rating_container.find('div', class_='star_fill')['style'].replace('width:', '').replace('%', '').strip()
  try:
      genre = cell.find('div', class_='game_genre').text.strip()
  except:
      genre = 'Unknown'

  print(i)
  print('Title:', title)
  print('Author:', author)
  print('Text:', text)
  print('Rating:', rating)
  print('Genre:', genre)
  print('=' * 50)
  print('')
    
```
