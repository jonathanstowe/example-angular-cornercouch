This is a reworked example for the CornerCouch module for AngularJS

    https://github.com/eddelplus/CornerCouch

You may have CouchDB available to install from your OS package manager
otherwise you can get it at:

    https://couchdb.apache.org/

You will also need to CouchApp installed to use this, you can find out 
about this at
  
     https://github.com/couchapp/couchapp

Assuming you have couchdb working and you have the python couchapp
installed you should just be able to push this to your database and
access the guestbook.html via the attachment to the design document.

Once you have cloned this to your local machine then you should be able
to:

    cd example-angular-cornercouch

    couchapp push http://localhost:5984/gbook 

Then you should be able to go to go to:

   http://127.0.0.1:5984/gbook/_design/example-angular-cornercouch/guestbook.html

If you want to use a different database name then you will need to edit the
_attachments/js/app.js to change the line:

	var db_name = 'gbook';

(which should be the first line of the file,) as appropriately.
     
You may want to add a user to try it out properly:

   curl -v -X PUT -H "Content-Type: application/json"  -d '{"type": "user", "roles": [], "name": "testuser", "password": "banana", "_id": "org.couchdb.user:testuser"}' http://localhost:5984/_users/org.couchdb.user:testuser

It's probably not wise to do this on a publicly available server and better
to change the 'testuser' and 'banana' in the above to some other values that
only you know. 

If you already have a publicly facing CouchDB server then hopefully you are
aware of the risks and have secured it appropriately. 

The version of angular-cornercouch.js that this uses may differ from the 
released version as I am using this to test changes that I make.

I've only tested this on Google Chrome and Firefox, personally I have no
interested in making it work on other browsers but if you do please feel
free to fork and send me a pull request when you have it working.

This example loads the AngularJS and Bootstrap resources from their
appropriate CDN sources - if this causes a problem for you you may want
to download the files to the _attachments/(js|css) directories and adjust
the locations in the html file appropriately.
