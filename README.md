# Project Demo

Realtime App with VueJS + RethinkDB + Socket + VueSocketio


Bons Liens:

https://www.rethinkdb.com/api/javascript/insert/ : Insert
https://www.rethinkdb.com/api/javascript/update/ : Update
https://www.rethinkdb.com/api/javascript/replace/: Replace
Replace documents in a table. Accepts a JSON document or a ReQL expression, and replaces the original document with the new one. The new document must have the same primary key as the original document.
https://www.rethinkdb.com/api/javascript/delete/: delete

Cursor for array: 
https://www.rethinkdb.com/api/javascript/each/
https://www.rethinkdb.com/api/javascript/to_array/

https://www.rethinkdb.com/api/javascript/db_create/
https://www.rethinkdb.com/api/javascript/db_drop/ 
https://www.rethinkdb.com/api/javascript/table_create/
https://www.rethinkdb.com/api/javascript/table_drop/




https://www.rethinkdb.com/api/javascript/match/ : Match




ReQL administration commands


Import:

sudo apt-get install python python-setuptools

easy_install --user pip

sudo pip install rethinkdb

rethinkdb import -f '/home
/boyer/Musique/datas.json'  -table cinema.users
 


 Export:
 
 rethinkdb dump -e cinema
 rethinkdb dump -e cinema.users



 Restore:

 rethinkdb restore rethinkdb_dump_2017-05-22T16:30:54.tar.gz


Conect Cinema + table users
 r.db("cinema").table('users')

Créer une table
r.db('cinema').tableCreate('comments')

Inserer:
r.db('cinema').table('comments').insert([
  {content: "blabla"}, 
  {content: "nice!!"},
]);


Modifier toute la liste
r.db('cinema').table('comments').update({dateCreated: new Date()})
r.db('cinema').table('comments').update({visible: false})


Juste one:
r.db('cinema').table('comments').filter({content: "nice!!"}).update({content: "Nice !!!!"})


Avec Regex:

r.db('cinema').table('comments').filter(function(doc){
    return doc('content').match("^bla")
}).update({content: "Super Blabla !!!!"})



Avec Regex:

r.db('cinema').table('comments').filter(function(doc){
    return doc('content').match("^bla")
}).update({content: "Super Blabla !!!!"})

Plus Regex

r.db('cinema').table('comments').filter(function(doc){
    return doc('content').match("(?i)^[a-z\! ]+$")
})