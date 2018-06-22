# Exercise B Nested Routes

We have a application with few routes. Now we are going to add nested routes.

Application is the main route, so it contains the routes created by us. We have a route called **invite-module, **we have to add three nested routes using the command cli:

```
ember generate route invite-module/index

ember generate route invite-module/find-users

ember generate route invite-module/show-invites
```

We have this structure:

![](/assets/nestedroutes1.png)

### By default every route render index route if it exists.

### ![](/assets/nested3.png)

![](/assets/nested4.png)

So, we can add styles for see this in our application.

If you want to add links to the nested routes, you will write some like this:

**invite-module.js **

```html
<nav class="navbar navbar-expand-lg navbar-light bg-light">
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
            <li class="nav-item">
            
                {{#link-to 'invite-module.show-invites' class="nav-link"}} Show Invites {{/link-to}}
                
            </li>
            <li class="nav-item">
            
                {{#link-to 'invite-module.find-users' class="nav-link"}} Show Invites {{/link-to}}
                
            </li>
        </ul>
    </div>
    {{#link-to 'invite-module' class="nav-link"}} Invite Module {{/link-to}}
</nav>

{{outlet}}
```

### This is important, because you have to structure your Ember App consider this.



