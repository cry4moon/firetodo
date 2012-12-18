Firetodo
========

A simple todo list app illustrating the use of server-signed tokens.

### [Live Demo](http://firebase.github.com/firetodo/)

How does it work?
-----------------
Firetodo manages the todo lists of three users, Alice, Bob, and Carol. The
data for each user is kept in Firebase under the root namespace underneath
their respective usernames. There is a simple server process that mimics a
server process that plugs into an existing user system. Rather than
provision users into Firebase or use one of the auth services compatible
with Firebase, the signed server tokens allows developers to use Firebase
with their existing users.

The server signs the "login" requests given its representation of the users,
as such:
  * Alice is the manager.
  * Bob and Carol are regular users.
  * Every other user is a guest.

The server process then signs the auth token with the Firebase secret for
the namespace and returns this token to the client. The client then uses it
in an auth() request to a Firebase reference.

The rules enforce the following semantics: managers can write to anyone's
todo list, Alice and Bob can write to their respective lists, and anyone can
write to Carol's list. When writing to Alice or Bob's lists, the from field
has to match the authenticated user.

The variety in the rules are meant to illustrate the flexibility one has in
creating Firebase security and validation rules.

Exercises for the reader
------------------------
  1. Augment front-end to support an arbitrary number of users.
  2. Include support for different flows depending on if the user is a manager,
regular user, or guest.
  3. Add real-time support for todo-completion, re-assignment, and commenting.

License
-------
No part of this project may be copied, modified, propagated, or distributed
except according to terms in the accompanying LICENSE file.
