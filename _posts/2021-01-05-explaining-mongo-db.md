---
title:  "Explaining mongodb"
layout: post
---

## What is mongodb?
`"MongoDB is a cross-platform document-oriented database program. Classified as a NoSQL database program"` let me show you how the structure looks like first:
| cluster  | database  | collection | document  | (schema) | the reason schema is in curly brackets is because an schema is not always needed, but lets start at the top
a cluster is basically a group of databases on an shared server, now everything what a database does is just have groups of collections.
It gets interesting on the collections, they hold the documents, but what are they? They are basically JSON files: but they are stored in the BSON form, its an binary format
giving you more types and what i would guess also: a better performance, else i wouldn't see the need of mongodb in the first place, but i think what makes mongodb awesome
is their queries what im going to talk about in the next section.

## Mongoose
Mongoose is an javascript library that enables you to write your own schemas, create objects with them, save them, and also query them.
But lets first of all understand what schemas are: they are basically an form to explain the contents of an document 
(you can have documents with a different schema in one collection). 

{% highlight js %}
const Cat = mongoose.model('Cat', { name: String });

const kitty = new Cat({ name: 'Zildjian' });
kitty.save().then(() => console.log('meow'));

console.log(await Cat.find({ name: 'Zildjian'}))
{% endhighlight %}

## typegoose
Now im not normally using javascript but typescript, a javascript superset but typed out. now theres no reason for me to use ts
if i dont actually use its "advantages", that would be first of all typing out the type of course, and shorter code:

{% highlight js %}
class KittenClass {
  @prop()
  public name?: string;
}

const Kitten = getModelForClass(KittenClass);

let document = await Kitten.create({ name: 'Kitty' });
{% endhighlight %}

This pretty much covers mongodb and its usecases.
