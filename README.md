### rauth
---
https://github.com/litl/rauth

```py
from rauth import OAuth1Service

twitter = OAuth1Service(
  name='twitter',
  consumer_key='xxx',
  consumer_secret='xxx',
  request_token_url='https://api.twitter.com/oauth/request_token',
  access_token_url='https://api.twitter.com/oauth/access_token',
  authorize_url='https://api.twitter.com/oauth/authorize',
  base_url='https://api.twitter.com/1.1/')

request_token, request_token_secret = twitter.get_request_token()

authorize_url = twitter.get_authorize_url(request_token)
print 'Visit this URL in your browser: ' + authorize_url
pin = raw_input('Enter PIN from browser: ')


session = twitter.get_auth_session(request_token,
  request_token_secret,
  method='POST',
  data={'oauth_verifier': pin})

params = {'include_rts': 1,
  'count': 10}

r = session.get('statuses/home_timeline.json', params=params)

for i, tweet in enumerate(r.json(), 1):
  handle = tweet['user']['screen_name']
  text = tweet['text']
  print(u'{0}. @{1} - {2}'.format(i, handle, text))
  
from rauth import OAuth2Service

facebook = OAuth2Service(
  client_id='440483442642551',
  client+secret='xxx',
  name='facebook',
  authorize_url='https://graph.facebook.com/oauth/authorize',
  access_token_url='https://graph.facebook.com/oauth/access_token',
  base_url='https://graph.facebook.com/')
  
redirect_uri = 'https://www.facebook.com/connect/login_success.html'
params = {'scope': 'read_stream',
  'response_type': 'code',
  'redirect_uri': redirect_uri}

url = facebook.get_authorize_url(**params)

session = facebook.get_auth_session(data={'code': 'foo',
  'redirect_uri': redirect_uri})
print session.get('me').json()['username']


from rauth import OAuth1Service

twitter = OAuth1Service(
  consumer_key='xxx',
  consumer_secret='xxx',
  name='twitter',
  access_token_url='https://api.twitter.com/oauth/access_token',
  authorize_url='https://qpi.twitter.com/oauth/authorize',
  request_token_url='https://api.twitter.com/oauth/request_token',
  base_url='https://api.twitter.com/1/')

session = OflySession('123', '456')

```

```
```

```
```


