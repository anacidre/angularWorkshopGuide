## Setting up our coffee menu - Our first component

Now that we have set up our first Angular app, we'll start making changes to develop our Hipster Coffee web.

We'll start developing our app, for now we'll be focus just in the menu that shows different types of coffee that can be ordered from the store. To do that we'll create a new component from scratch.
At the end of this section we had built the skeleton for the section highlighted in blue below:

![picture](https://github.com/Vero333/angularWorkshopGuide/blob/master/guideResources/images/coffe-order-app.jpg)


We can use angular CLI to help us to create an Angular component and we'll see that later but, for the first one, we are going to do it in the hard way ;)

But before that let's create the Coffee class:

Create a folder named shared under the coffee-order-app/src/app/ folder:

```
cd coffee-order-app/src/app/
mkdir shared
cd shared
```

This folder will contain the definition of the Coffee class:

```
export class Coffee {
  name: string;
  image: string;
  price: string;
}
```

At the menu page will be showing images representing the different coffee types, so let's create the folder where those images will be held:

```
cd coffee-order-app/src/
mkdir assets
cd assets
mkdir images
```

And save the images there.
Markup :  [coffeImages.zip](https://github.com/Vero333/angularWorkshopGuide/raw/master/guideResources/images/coffeeImages.zip)

Now we are ready to start with our coffee-menu component.
First let's create the folder that will contain it. The folder name will match the component name and it should be located at coffee-order-app/src/app/:

```
cd coffee-order-app/src/app/
mkdir coffee-menu
cd coffee-menu
```

Inside of this folder we need to create three files:
* coffee-menu.component.ts: controller
* coffee-menu.component.html: template
* coffee-menu.component.scss: style


coffee-menu.component.ts:

```
import { Component, OnInit } from '@angular/core';

import { Coffee } from '../shared/coffee';

@Component({
  selector: 'coffee-menu',
  templateUrl: './coffee-menu.component.html',
  styleUrls: ['./coffee-menu.component.scss']
})

export class CoffeeMenuComponent implements OnInit {

  coffees: Coffee[] = [
    {
      name:'Flat white',
      image: '/assets/images/flatWhite.png',
      price:'1.50'
    },
    {
      name:'Capuccino',
      image: '/assets/images/capuccino.png',
      price:'2.50'
    },
    {
      name:'CaramelMachiato',
      image: '/assets/images/caramelMachiato.png',
      price:'3.00'
    },
    {
      name:'Expresso',
      image: '/assets/images/expresso.png',
      price:'2.50'
    }
  ];

  constructor() { }

  ngOnInit() { }
}
```

In our template we'll be using angular material, it needs to be installed using the command specified below:

```
npm install @angular/material@latest --save
npm install @angular/cdk@latest --save
```

coffee-menu.component.html

```
<div class="coffee-menu">
  <mat-grid-list cols="2" rowHeight="2:1">
    <mat-grid-tile *ngFor="let coffee of coffees">
      <mat-grid-tile-header>
        <h2 mat-line>{{coffee.name}}</h2>
      </mat-grid-tile-header>
      <img src={{coffee.image}} alt={{coffee.name}}>
      <mat-grid-tile-footer>
        <span mat-line>Price: {{coffee.price}}</span>
      </mat-grid-tile-footer>
    </mat-grid-tile>
  </mat-grid-list>
  <a href="https://www.freepik.com/free-vector/coffee-types_803190.htm">Designed by Freepik</a>
</div>
```

coffee-menu.component.scss

```

```

Now we need to modify the file app.module.ts

```
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { BrowserAnimationsModule } from '@angular/platform-browser/animations';
import { MatGridListModule } from '@angular/material/grid-list';

import { AppComponent } from './app.component';

import { CoffeeMenuComponent } from './coffee-menu/coffee-menu.component';

@NgModule({
  declarations: [
    AppComponent,
    CoffeeMenuComponent
  ],
  imports: [
    BrowserModule,
    BrowserAnimationsModule,
    MatGridListModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }

```

Finally let's modify the file app.component.html to reference the coffee-menu component:

```
<coffee-menu></coffee-menu>
```

And the coffee-menu.component.scss to specify the background colour:

```
.coffee-menu {
    background-color: #915e4c;
}
```
