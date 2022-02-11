# Essential Feed App

## Example -unclear- Story
As a user
I want the app to load the feed
So I can see the feed

## Acceptance criteria
Given a user
When the user opens the feed
Then the feed is displayed

## Questions
- What should happen when the connection fails? What if the customer is offline?
- Should we cache the feed to provide a delightful offline experience?
- For how long can we cache the feed?
- What should happen if the customer is offline and there's no cache?

#### Note to Developers

- Don't be afraid to be looked silly or lossing credability, because it's for your own sake and your team
- We asked question with goals to improve the requirements and, as a side effect, build trust
- As developers, it's our job to help the business understand the technical challanges

## BDD Specs

### Story: Customer requests to see the feed

### Narative #1

```
As an online customer
I want the app to automatically load my latest image feed
So I can always enjoy the newest images of my friends
```

#### Scenarios (Acceptance criteria)

```
Given the customer has connectivity
When the customer requests to see the feed
Then the app should display the latest feed from remote
And replace the cache with the new feed
```

### Narative #2

```
As an offline customer
I want the app to show the latest saved version of my image feed
So I can always enjoy images of my friends
```

#### Scenarios (Acceptance criteria)

```
Given the customer doesn't have connectivity
When the customer requests to see the feed
Then the app should display the latest feed saved

Given the customer doesn't have connectivity
And the cache is empty
When the customer requests to see the feed
Then the app should display an error message
```



## Use Cases

### Load Feed

#### Data
- URL

#### Primary course (happy path):
1. Execute "Load Feed Items" command with above data.
2. System downloads from the URL.
3. System validates downloaded data.
4. System creates feed items from valid data.
5. System delivers feed items.

#### Invalid data - error course (sad path):
1. System delivers error


### No connectivity - error course (sad path):
1. System   error


---
### Load Feed Fallback (Cache)

#### Data
- Max age

#### Primary course:
1. Execute "Retrieve Items" command with above data.
2. System fetches feed data from cache.
3. System creates feed items from cached data.
4. System delivers feed items.

#### No cache course (sad path):
1. System delivers no feed items.


---
### Save Feed Items

#### Data
- Feed items

#### Primary course (happy path):
1. Execute "Save Feed Items" command with above data.
2. System encodes feed items.
3. System timestamps the new cache.
4. System replaces the cache with new data.
5. System delivers success message.
