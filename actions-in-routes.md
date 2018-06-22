Actions in Routes

> “Event handlers transform DOM events to user intent. Clicking a link is interpreted as wanting to go to the URL indicated by the link; clicking a button is understood as creating something where the name is taken from a text field. The classic way that Ember provides for this is through **actions**.”
>
> Excerpt From: Balint Erdi. “Rock and Roll with Ember.js 2”

The actions have effect over the route template.![](/assets/route-anatomy.png)

```js
import Route from '@ember/routing/route';

export default Route.extend({

    model(){

    },

    actions:{

    }

});
```



