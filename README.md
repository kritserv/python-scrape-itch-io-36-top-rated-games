# Scrape Data From itch.io 36 top rated games 
https://itch.io/games/top-rated

A python code for scraping title author text rating genre from top 36 rated games on itch.io using BeautifulSoup and requests

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

# Result
```
1
Title: HoloCure
Author: Kay Yu
Text: A 'survivors' like, free unofficial Hololive fan game!
Rating: 98.96478
Genre: Action
==================================================

2
Title: Our Life: Beginnings & Always
Author: GBPatch
Text: Grow from childhood to adulthood with the lonely boy next door in this near-fully customizable visual novel.
Rating: 98.93347
Genre: Visual Novel
==================================================

3
Title: Adventures With Anxiety!
Author: Nicky Case!
Text: An interactive story about anxiety. You play *as* the anxiety
Rating: 98.16080
Genre: Visual Novel
==================================================

4
Title: Butterfly Soup
Author: Brianna Lei
Text: Gay girls playing baseball and falling in love
Rating: 97.82547
Genre: Visual Novel
==================================================

5
Title: Friday Night Funkin'
Author: ninjamuffin99
Text: The coolest rhythm game
Rating: 94.52002
Genre: Rhythm
==================================================

6
Title: A Short Hike$7.99
Author: adamgryu
Text: a little exploration game about hiking up a mountain
Rating: 97.73874
Genre: Adventure
==================================================

7
Title: Blooming Panic
Author: robobarbie
Text: Welcome to our server!
Rating: 98.64048
Genre: Visual Novel
==================================================

8
Title: Project Kat
Author: Leef 6010
Text: A small, unconventional horror rpg.
Rating: 96.66846
Genre: Role Playing
==================================================

9
Title: Doki Doki Literature Club!
Author: Team Salvato
Text: Will you write the way into her heart?
Rating: 96.18679
Genre: Visual Novel
==================================================

10
Title: Andromeda Six
Author: Wanderlust Games
Text: A sci-fi themed Visual Novel game.
Rating: 97.41194
Genre: Visual Novel
==================================================

11
Title: We Become What We Behold
Author: Nicky Case!
Text: a game about news cycles, vicious cycles, infinite cycles
Rating: 95.51327
Genre: Unknown
==================================================

12
Title: DELTARUNE
Author: tobyfox
Text: UNDERTALE's parallel story
Rating: 99.07223
Genre: Role Playing
==================================================

13
Title: goodbye, doggy
Author: Picogram
Text: Help your family cope with your death as a ghostly dog!
Rating: 97.10339
Genre: Puzzle
==================================================

14
Title: Sort the Court!
Author: Graeme Borland
Text: Give your decree in simple yes or no answers, and help the kingdom grow!
Rating: 93.99833
Genre: Simulation
==================================================

15
Title: Celeste$19.99
Author: Maddy Makes Games
Text: Brave hundreds of hand-crafted challenges as you help Madeline survive her journey to the top of Celeste Mountain!
Rating: 97.64156
Genre: Platformer
==================================================

16
Title: Six Cats Under
Author: Team Bean Loop
Text: You died. Your unfinished business? The fate of your many cats!
Rating: 95.57808
Genre: Puzzle
==================================================

17
Title: Our Life: Now & Forever
Author: GBPatch
Text: A paper airplane, two new neighbors, four autumns, and a one of a kind life.
Rating: 99.21288
Genre: Visual Novel
==================================================

18
Title: 1998 - Found Footage Backroom Horror Game FREE (Microphone Sensitive Demo Game)
Author: Steelkrill Studio
Text: Now you will see what really lies in the backrooms, with this found footage style horror game.
Rating: 98.29630
Genre: Adventure
==================================================

19
Title: Backpack Hero$16.99
Author: Thejaspel
Text: Collect rare items, organize your backpack, and defeat the dungeon!
Rating: 97.03947
Genre: Role Playing
==================================================

20
Title: Night in the Woods$19.99
Author: Finji
Text: At the end of everything, hold onto anything.
Rating: 96.25056
Genre: Adventure
==================================================

21
Title: A Tale of Crowns
Author: cherry
Text: A Middle Eastern fantasy/romance story.
Rating: 97.64628
Genre: Interactive Fiction
==================================================

22
Title: ERROR143
Author: Jenny Vi Pham
Text: A fully voiced bickering-and-bantering rivals-to-lovers visual novel <3
Rating: 97.40162
Genre: Visual Novel
==================================================

23
Title: Vincent: The Secret of Myers-30%
Author: dino999z
Text: A horror adventure visual novel with point & click components
Rating: 98.94636
Genre: Visual Novel
==================================================

24
Title: When The Night Comes$9.09-30%
Author: Lunaris Games
Text: When the night comes, death follows...
Rating: 96.61507
Genre: Visual Novel
==================================================

25
Title: Mindustry
Author: Anuke
Text: The automation tower defense game
Rating: 96.57452
Genre: Strategy
==================================================

26
Title: Cinderella Phenomenon
Author: Dicesuki
Text: Cinderella Phenomenon is a free otome game that was inspired by various popular fairy tales.
Rating: 96.33143
Genre: Visual Novel
==================================================

27
Title: The Legend Of The Last Dragon$4.94-62%
Author: Zef1r0
Text: An indie fantasy RPG game inspired by the great classics of the past!
Rating: 99.66154
Genre: Role Playing
==================================================

28
Title: missed messages.
Author: angela he
Text: ‘goth gf’s iPhone’ airdrops you - accept or decline? A love/horror story about life, death, & memes.
Rating: 95.81633
Genre: Visual Novel
==================================================

29
Title: Ebon Light
Author: Underbliss
Text: A dark tale of old secrets and romance!
Rating: 96.74419
Genre: Visual Novel
==================================================

30
Title: Therapy with Dr. Albert Krueger-30%
Author: dino999z
Text: Sign up for your therapy today!
Rating: 96.26230
Genre: Interactive Fiction
==================================================

31
Title: Scout: An Apocalypse Story
Author: Anya
Text: A text choice romance in an apocalyptic setting.
Rating: 97.35950
Genre: Interactive Fiction
==================================================

32
Title: Wayfarer
Author: Idrelle Games
Text: Marked by complete magical immunity, Wayfarers wander the world, fighting magic. Where will your fate lead you?
Rating: 98.13126
Genre: Interactive Fiction
==================================================

33
Title: Lookouts
Author: paranoidhawk
Text: A fateful meeting of queer outlaws in the desert.
Rating: 97.62646
Genre: Visual Novel
==================================================

34
Title: Vampire Survivors
Author: poncle
Text: Mow thousands of night creatures and survive until dawn!
Rating: 97.09818
Genre: Action
==================================================

35
Title: BloodbornePSX
Author: LWMedia
Text: Relive the first few hours of the PS4 classic, rebuilt with PS1 aesthetics!
Rating: 97.71930
Genre: Action
==================================================

36
Title: Coming Out Simulator 2014
Author: Nicky Case!
Text: a half-true story about half-truths
Rating: 94.55227
Genre: Unknown
==================================================
```
