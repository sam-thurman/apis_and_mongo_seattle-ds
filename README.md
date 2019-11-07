This repository contains information about using APIs and MongoDB in collecting and storing data. It was designed for pedagogical purposes and began life as a fork of Miles Erickson's repository about APIs. His instructions for registering for the Foursquare API are detailed below.

# Foursquare API Example

## Register

* Please [register for the Foursquare API](https://foursquare.com/developers/apps) and create an app. When you create the app, you can indicate that you're affiliated with Flatiron School and that you're a student. 
* Create a file called `.secrets/credentials.json` based on `.secrets/credentials-example.json`
  ```
  cd .secrets
  cp credentials-example.json credentials.json
  vim credentials.json  # use your favorite editor to paste in your client ID and client secret
  cd ..
  git status  # credentials.json should not show up because .secrets/ is in .gitignore
  ```

## Review Documentation

* https://developer.foursquare.com/docs/api/venues/search

## Example API Request

```python
import json
import requests

# Load secrets from credentials.json
url = 'https://api.foursquare.com/v2/venues/explore'
with open('.secrets/credentials.json') as f:
    params = json.load(f)
    
params['v'] = '20180323'
params['ll'] = '40.7243,-74.0018',
params['query'] = 'coffee',
params['limit'] = 1

response = requests.get(url=url, params=params)
data = json.loads(response.text)
```
