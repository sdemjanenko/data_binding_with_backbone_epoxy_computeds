Data Binding With Backbone Epoxy Computeds
==========================================

Data Binding
------------

Data binding is tying the DOM to the model data such that bound input field
changes propagate to the bound model and updates to the model from the server get
propagated to the input field.  This is an example of two-way data binding because
the model can update the input and the input can update the model.

One-way data binding is when a non-input field displays a value from a model.  Any time
the model changes, the DOM gets updated.



Backbone.Epoxy
==============

Backbone Epoxy is an extension to Backbone that adds one-way and two-way data binding.
Epoxy adds the constructors Backbone.Epoxy.Model and Backbone.Epoxy.View.


Computeds
---------

Epoxy introduces the idea of a "computed" to help render model data in complicated ways.
It does this by changing the .get() function on Backbone.Model to track dependencies within
a computed function.

    var User = Backbone.Epoxy.Model.extend({
      defaults: {
        firstName: '',
        lastName: ''
      },
      computeds: {
        fullName: function() {
          return this.get('firstName') + ' ' + this.get('lastName');
        }
      }
    });


In the above example, I added the fullName helper method.  By making it a computed, I can use the
fullName function in an Backbone.Epoxy.View and any time firstName or lastName changes, the view
will update the DOM attached to the fullName method.


Other Libraries
===============

Backbone.Epoxy is not the only data-binding library out there.  In my opinion it is the best
but it would be well worth your time to check out a couple of the others.

- [Rivets](http://rivetsjs.com/)
- [Backbone.stickit](http://nytimes.github.io/backbone.stickit/)
