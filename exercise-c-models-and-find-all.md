# Exercise C: Models and Find All

We are going to develop a simple view, render a list of objects with **ember data and ember mirage.**

1.- In out application we have to create a model:

> ember generate model invite

2.- Add some attributes

```js
import DS from 'ember-data';

export default DS.Model.extend({
  user: DS.attr('string'),
  dateCreated: DS.attr('date'),
  status: DS.attr('string')
});
```

3.- Go to your route **invite-modules/show-invites.js **

```js
import Route from '@ember/routing/route';

export default Route.extend({


  model(){

      return this.get('store').findAll('invite');

  }


});
```

At this point we have a model **invite**, and in route **show-invites** we are going to get all invites.

And you will have a GET request for find all invites:

```bash
Request URL:http://localhost:4200/invites
Request Method:GET
Status Code:404 Not Found
Remote Address:[::1]:4200
Referrer Policy:no-referrer-when-downgrade
```

We have to install the **ember-mirage** and add a fixture for respond to`/invites`

For install ember mirage:

```
ember install ember-cli-mirage
```

Create a fixture called **invites**

```
ember generate mirage-fixture invites
```

**mirage/fixtures/users.js**

```js
export default [
  {id:1, user:"fake user 1", dateCreated:1519283297836, status:"invited"},
  {id:2, user:"fake user 2", dateCreated:1519283297836, status:"canceled"},
  {id:3, user:"fake user 3", dateCreated:1519283297836, status:"reinvited"},
  {id:4, user:"fake user 4", dateCreated:1519283297836, status:"invited"},
  {id:5, user:"fake user 5", dateCreated:1519283297836, status:"reinvited"},
  {id:6, user:"fake user 6", dateCreated:1519283297836, status:"invited"},
  {id:7, user:"fake user 7", dateCreated:1519283297836, status:"answered"},
  {id:8, user:"fake user 8", dateCreated:1519283297836, status:"answered"},
  {id:9, user:"fake user 9", dateCreated:1519283297836, status:"invited"},
  {id:10, user:"fake user 10", dateCreated:1519283297836, status:"answered"}
];
```

This list of fixtures correspond to your model **invite**

Then, we have to load the fixture, add a Rest serializer, and add in mirage config.

**mirage/scenarios/default.js**

```js
export default function( server ) {

  server.loadFixtures('invites');
  server.loadFixtures('users');

}
```

**mirage/serializers/application.js**

```js
import { RestSerializer } from 'ember-cli-mirage';

export default RestSerializer.extend({
});
```

**mirage/config.js**

```js
export default function() {

  this.get('/invites');

}
```

Now we are getting all invites models in **invite-modules/show-invites.js **route.

We can use handlebars for show this model.

```handlebars
<div class="text-center">
  <br><h2> Invites </h2>
  <p>We are going to show all invites.</p><br>
</div>

<div class="row">
  <div class="col-md-6 offset-md-3">
    <table class="table table-sm table-hover">
      <thead>
        <tr>
          <th scope="col">User Invited</th>
          <th scope="col">Date</th>
          <th scope="col">Status</th>
        </tr>
      </thead>
      <tbody>
        {{#each model as |invite|}}
        <tr>
          <td> {{invite.user}} </td>
          <td> {{invite.dateCreated}} </td>
          <td> {{invite.status}} </td>
        </tr>
        {{/each}}
      </tbody>
    </table>
  </div>
</div>
```

Model is the result returning in **model \(\)** hook.![](/assets/getting.png)

