# Spotibulk

## Info

- Supports fetching a very high number of spotify song ids (tested to 2 million, though it took a while)
- Uses a Breath-first search approach on artists' related artists to gradually expand the search space
- Provides several parameters to adjust the search behavior, allowing you to fine-tune the app based on your needs (See usage for details)
- The primary script can be easily modified to fetch albums or artists

## Install

To start, either
- Clone into this repository in your project (```git clone https://github.com/alexhamidi/Spotibulk.git```)
- Copy and paste the content of 'index.txt' into a local file that you want to use to execute searches

After this, you need to install aiohttp:
```python
pip3 install aiohttp
```

## Usage

### Example

```python
from index import generate_songs

async def main():
    seed_ids = [
        '0iEtIxbK0KxaSlF7G42ZOp',  # Travis Scott
        '5K4W6rqBFWDnAN6FQUkS6x',  # Ye
        '699OTQXzgjhIYAHMy9RyPD',  # Carti
    ]

    trap_song_ids = await generate_songs(seed_ids, search_depth=2, max_albums_per_artist=1)

    print(f"ids retreived succesfully, {len(trap_song_ids)} ids in the list. First 5 items: {trap_song_ids[:5]}")

asyncio.run(main())

```
