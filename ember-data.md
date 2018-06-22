# Ember Data

Ember Data Library help us to create models and request.

The route anatomy looks like this:![](/assets/route-anatomy.png)

Until now, we have created routes, modify the templates, and render the views through link-to helper.

As a web app, every view have the possibility to manage data. For this we can take this data in the** model\( \), **contained in the current route js file.

#### Models

> **Models are objects that represent the underlying data that your application presents to the user**. Different apps will have very different models, depending on what problems they're trying to solve.
>
> A model** is a class that defines the properties and behavior of the data that you present to the user.** Anything that the user expects to see if they leave your app and come back later \(or if they refresh the page\) should be represented by a model.

Ember Cli help us to create the model, a simple model looks like:

> ember generate model person

**app/models/person.js**

```js
import DS from 'ember-data';

export default DS.Model.extend({
  name: DS.attr('string'),
  age: DS.attr('number'),
  admin: DS.attr('boolean')
});
```

When you has created a model, you can start to operate with ember data.

### Finding Models

```js
let person = this.get('store').findRecord('person', 1); // => GET /persons/1 by Path Variable

let person = this.get('store').findRecord('person', {"username":"carlogilmar"}); // => GET by Query Params

let people = this.get('store').findAll('person'); // => GET /persons

```

Ember conventions by default wait for response as this:

```js
{
	"person": [{
			"id": 1,
			"name": "carlogilmar",
			"age": 21,
			"admin": false
		},
		{
			"id": 2,
			"name": "cgg888jorge",
			"age": 22,
			"admin": true
		},
		{
			"id": 3,
			"name": "neodevelop",
			"age": 23,
			"admin": false
		},
		{
			"id": 4,
			"name": "leovergara",
			"age": 24,
			"admin": true
		}
	]
}
```

If you want to receive the response with other format, you have to create your own** serializer.**

### Create and save Models 

```js
let newPerson = this.get('store').createRecord('person', {
  name: 'Gamaliel',
  age: 26,
  admin: false
});

newPerson.save();  //=> POST to '/persons'
```

### Update Models

```js
this.get('store').findRecord('person', 1).then(function(person) {

  person.get('name'); // => "carlogilmar"

  person.set('name', 'Carlo Gilmar Padilla Santana');

  person.save(); // => PATCH to '/person/1'
  
});
```

### Delete Models

```js
this.get('store').findRecord('person', 1).then(function(person) {

  person.deleteRecord();

  person.get('isDeleted'); // => true
  
  person.save(); // => DELETE to /persons/1
  
});
```



