# Render Templates

```
We are going to review:
    Handlebars basics
    Handlebars and Ember
    Routes and templates
```

## Handlebars Basics

Ember use the project Handlebars for render views.

> Handlebars provides the power necessary to let you build **semantic templates **effectively with no frustration.

You have a file hbs, which contains html content and handlebars expressions identifyed by:

**example.hbs**

```handlebars
<div class="entry">
  <h1>{{title}}</h1>
  <div class="body">
    {{body}}
  </div>
</div>
```

Using only javascript, for create the view you have to write this:

```js
var source   = document.getElementById("entry-template").innerHTML;
var template = Handlebars.compile(source);
var context = {title: "My New Post", body: "This is my first post!"};  // Context for fill the template
var html    = template(context);
```

And the view compiled will looks like this:

```handlebars
<div class="entry">
  <h1>My New Post</h1>
  <div class="body">
    This is my first post!
  </div>
</div>
```

Ember use this for render views.

## Handlebars and Ember

A route contains route js file, and handlebars template, both with the same name.

The  **application.hbs,** which render the first and main view, have:

```handlebars
{{!-- The following component displays Ember's default welcome message. --}}
{{welcome-page}}
{{!-- Feel free to remove this! --}}

{{outlet}}
```

In ember we can create routes and nested routes. By default, the main route is application \(although it doesn't have a js file\). As routes, the templates could be nested.

For made this, you have to use: **outlet**.

**This expression means that here is going to render the nested routes.   
**

When you go to **localhost:4200** you will only see the **application template**. But when you go to **localhost:4200/invite-module** you will see the **invite-module template** into the application template.

![](/assets/outlet.png)

![](/assets/templatesnested.png)

## Routes and templates

The route anatomy is the relationship between the route and the template.

![](/assets/route-anatomy.png)

```js
import Route from '@ember/routing/route';

export default Route.extend({

    model(){
    
    },
    
    actions:{
    
    }
    
});
```

Your route \(js file\) contains a** model hook,** where you can load data for render in the template, and the template can access to the **actions, ember functions**, for example, with buttons or forms.

