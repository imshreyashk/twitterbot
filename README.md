# twitterbot

import tweepy 
from time import sleep 
from credentials import * 
from config import QUERY, FOLLOW, LIKE, SLEEP_TIME 

consumer_key = '' 
consumer_secret = '' 
access_token = '' 
access_token_secret = ''

# This is hastag which Twitter bot will 
# search and retweet You can edit this with 
# any hastag .For example : '# javascript' 

QUERY = '# anything'

# Twitter bot setting for liking Tweets 
LIKE = True

# Twitter bot setting for following user who tweeted 
FOLLOW = True

# Twitter bot sleep time settings in seconds. 
# For example SLEEP_TIME = 300 means 5 minutes. 
# Please, use large delay if you are running bot 
# all the time so that your account does not 
# get banned. 

SLEEP_TIME = 300

# This is just a sample file. You need to 
# edit this file. You need to get these 
# details from your Twitter app settings. 
  
auth = tweepy.OAuthHandler(consumer_key, consumer_secret) 
auth.set_access_token(access_token, access_token_secret) 
api = tweepy.API(auth) 
  
print("Twitter bot which retweets, like tweets and follow users") 
print("Bot Settings") 
print("Like Tweets :", LIKE) 
print("Follow users :", FOLLOW) 
  
for tweet in tweepy.Cursor(api.search, q = QUERY).items(): 
    try: 
        print('\nTweet by: @' + tweet.user.screen_name) 
  
        tweet.retweet() 
        print('Retweeted the tweet') 
  
        # Favorite the tweet 
        if LIKE: 
            tweet.favorite() 
            print('Favorited the tweet') 
  
        # Follow the user who tweeted 
        # check that bot is not already following the user 
        if FOLLOW: 
            if not tweet.user.following: 
                tweet.user.follow() 
                print('Followed the user') 
  
        sleep(SLEEP_TIME) 
  
    except tweepy.TweepError as e: 
        print(e.reason) 
  
    except StopIteration: 
        break

    # Edit this config.py file as you like 

# This is hastag which Twitter bot will 
# search and retweet You can edit this with 
# any hastag .For example : '# javascript' 

QUERY = '# anything'

# Twitter bot setting for liking Tweets 
LIKE = True

# Twitter bot setting for following user who tweeted 
FOLLOW = True

# Twitter bot sleep time settings in seconds. 
# For example SLEEP_TIME = 300 means 5 minutes. 
# Please, use large delay if you are running bot 
# all the time so that your account does not 
# get banned. 

SLEEP_TIME = 300

# This is just a sample file. You need to 
# edit this file. You need to get these 
# details from your Twitter app settings. 


