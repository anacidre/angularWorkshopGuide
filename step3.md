## Creating our second component using Angular CLI

At the end of this section we should have developed a new component for the footer that shows the total price:

![picture](https://github.com/Vero333/angularWorkshopGuide/blob/master/guideResources/images/xxx.jpg)

For now, the price will be a static value, but in the next section will see how this value can be updated depending on the coffees purchased by the client.

This time the component will be generated using Angular CLI. So let's go to the Terminal and at coffee-order-app type:

```
ng generate component footer
```

This will create the necessary files for the component in the footer folder and also import this component into app.module.ts.

If we add the component in the app.component.html page we can see our footer in the page:

```
<coffee-menu></coffee-menu>
<app-footer></app-footer>
```

Now let's change the component a little bit so it reflects the information that we want to show to our users.

First let's create an attribute that will contain the final price (footer.component.ts).

```
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-footer',
  templateUrl: './footer.component.html',
  styleUrls: ['./footer.component.scss']
})
export class FooterComponent implements OnInit {
  price: number = 12;

  constructor() { }

  ngOnInit() {
  }

}
```

We need to modify the html for our footer component:

```
<div class="footer">
  <h3>Price: {{price}}</h3>
</div>
```

Add finally change the styles in the footer.component.scss:
```
.footer {
    background-color: #71dad1;
    display:inline-block;
    width: 100%;
}
```
