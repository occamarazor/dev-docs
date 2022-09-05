# MongoDB Cheat Sheet

## Check version
```
mongosh --version
```

## Show All Databases
```
show dbs
```

## Show Current Database
```
db
```

## Create Or Switch Database
```
use blog
```

## Drop Database
```
db.dropDatabase()
```

## Create Collection
```
db.createCollection('posts')
```

## Show Collections
```
show collections
```

## Drop Collection
```
db.posts.drop()
```

## Insert Document
```
db.posts.insertOne({
  title: 'Post 1',
  body: 'Body of post 1',
  category: 'News',
  likes: 1,
  tags: ['news', 'events'],
  date: Date()
})
```

## Insert Multiple Documents
```
db.posts.insertMany([
  {
    title: 'Post 2',
    body: 'Body of post 2',
    category: 'Event',
    likes: 2,
    tags: ['news', 'events'],
    date: Date()
  },
  {
    title: 'Post 3',
    body: 'Body of post 3',
    category: 'Tech',
    likes: 3,
    tags: ['news', 'events'],
    date: Date()
  },
  {
    title: 'Post 4',
    body: 'Body of post 4',
    category: 'Event',
    likes: 4,
    tags: ['news', 'events'],
    date: Date()
  },
  {
    title: 'Post 5',
    body: 'Body of post 5',
    category: 'News',
    likes: 5,
    tags: ['news', 'events'],
    date: Date()
  },
])
```

## Find All Documents
```
db.posts.find()
```

## Find Documents with Query
```
db.posts.find({category: 'News'})
```

## Find Specific Fields
```
db.posts.find({ title: 'Post 1' }, {
  tags: [ 'news', 'events' ],
  likes: 1
})
```

## Find One Document
```
db.posts.findOne({ category: 'News' })
```

## Sort Documents
### Ascending
```
db.posts.find().sort({ title: 1 })
```

### Descending
```
db.posts.find().sort({ title: -1 })
```

## Count Documents
```
db.posts.countDocuments()
db.posts.estimatedDocumentCount()
db.posts.countDocuments({ category: 'News' })
```

## Limit Documents
```
db.posts.find().limit(2)
```

## Chaining
```
db.posts.find().limit(2).sort({ title: -1 })
```

## Foreach
```
db.posts.find().forEach((doc) => {
  print("Blog Post: " + doc.title)
})
```

## Update Document ($set)
```
db.posts.updateOne({ title: 'Post 1' },
{
  $set: {
    body: 'Body for post 1 NEW!',
    category: 'Tech'
  }
})
```

## Update Document or Insert if not found
```
db.posts.updateOne({ title: 'Post 6' },
{
  $set: {
    title: 'Post 6',
    body: 'Body of post 6',
    category: 'News'
  },
},
{
  upsert: true
})
```

## Update Multiple Documents
```
db.posts.updateMany({}, {
  $inc: {
    likes: 1
  }
})
```

## Increment Field ($inc)
```
db.posts.updateOne({ title: 'Post 1' },
{
  $inc: {
    likes: 2
  }
})
```

## Rename Field ($rename)
```
db.posts.updateOne({ title: 'Post 2' },
{
  $rename: {
    likes: 'views'
  }
})
```

## Delete Document
```
db.posts.deleteOne({ title: 'Post 6' })
```

## Delete Multiple Documents
```
db.posts.deleteMany({ category: 'Tech' })
```

## Greater & Less Than
```
db.posts.find({ views: { $gt: 2 } })
db.posts.find({ views: { $gte: 7 } })
db.posts.find({ views: { $lt: 7 } })
db.posts.find({ views: { $lte: 7 } })
```

## TODO: Aggregation