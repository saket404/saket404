---
layout: single
title: "Access Dota game statistics using Python"
excerpt: "Learn how to access your Dota 2 statistics using OpenDota API with Python."
date: 2020-07-18
last_modified_at: 2020-07-18
header:
  overlay_image: /assets/images/posts/dota-part1/dota_gameplay.jpg
  overlay_filter: 0.8
tags:
  - Python
  - Dota
  - Guide
category:
  - Python
share: true
---
Recently I came across [OpenDota](https://www.opendota.com){:target="_blank"} which is an open source platform where you can analyse and visualise you game stats. My goal today is to show you how to setup your OpenDota account to be able extract data using Python. This can be done with other programming languages but it is particulary useful doing this in Python as you can further perform analysis on your or other pro gamers statitics through the API using various Data Analysis libraries. 

### OpenDota API
---
The [OpenDota API](https://www.opendota.com/api-keys){:target="_blank"} is built upon the main OpenDota platform. You can find the [documentation here](https://docs.opendota.com){:target="_blank"}. The documentation is nicely written and easy to follow.

![OpenDota docs](/assets/images/posts/dota-part1/opendota_docs.png "Open Dota docs")


To use the OpenDota API to access your stats, you would first need to setup your account to be available on OpenDota platform. This can be done with 2 simple steps. 

#### Step 1: Sign in on OpenDota

In order to let OpenDota calibrate your stats you will need to go the [OpenDota portal](https://www.opendota.com){:target="_blank"} and sign in using your Steam account. OpenDota will automatically parse you games and extract statistics. 

![OpenDota Steam Login](/assets/images/posts/dota-part1/opendota_login.png "Steam Login on OpenDota")

### Step 2: Retireve Account ID

To access your stats through the API we can see it requires an `account_id` which can be easily extracted once you login to the main OpenDota portal using your steam account. Your `account_id` will be seen on the website address which you can easily extract. 

![OpenDota docs](/assets/images/posts/dota-part1/steamID.png "Open Dota docs")

**Thats all we need! Now lets do some programming!**

### Extracting Data
---
With my steamID and the API path from the documentation, I have everything I need to extract my game data using Python. I will be using the `requests` library to access the endpoint. 
```python
import requests
import json
link = 'https://api.opendota.com/api/players/98166081/matches'
r = requests.get(link)
data = json.loads(r.text)
```
The code above extracts data regarding all the matches played by me from the `matches` endpoint ([docs here](https://docs.opendota.com/#tag/players%2Fpaths%2F~1players~1%7Baccount_id%7D~1matches%2Fget){:target="_blank"}). There are a vast amount of endpoints you can utilise to extract data which can be read about in the documentation. Given the response is a JSON I used `json` library to parse the data into JSON format. I always use `pandas` to manipulate data, just because how easy the library usage is and the abundance of features it provides. 

```python
import pandas as pd
df = pd.DataFrame(data)
df.head(10)
```
Voilà!, you have access to all your game stats now.

Output:

![dataframe](/assets/images/posts/dota-part1/dataAPI.png)

---
<iframe src="https://giphy.com/embed/zcCGBRQshGdt6" width="480" height="308" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/reaction-office-space-that-was-easy-zcCGBRQshGdt6">via GIPHY</a></p>

Happy Coding, Cheers!







