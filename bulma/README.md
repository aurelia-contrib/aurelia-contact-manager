# Aurelia Contact Manager Tutorial

This repo contains an implementation of the [Aurelia Framework Contact Manager Tutorial](http://aurelia.io/docs/tutorials/creating-a-contact-manager) using [Bulma](http://bulma.io)
for the css.

## Bulma
The finished application...
![The Finished Product](/contact-manager-bulma.png)


### Install Bulma

```
yarn add bulma 
``` 

or 

```
npm install bulma
```

### Import into Main.ts
```typescript 
import 'bulma/css/bulma.css';
```

## Font Awesome

Font Awesome is also required to display the icon in the nav bar at the top of the app.
it can be installed using  

### Install Font Awesome
``` yarn add font-awesome ``` or ``` npm install --save font-awesome ``` 

### Import into Main.ts

```typescript
import 'font-awesome/css/font-awesome.css';
```
just below where Bulma is imported into the file. 

## App Shell

### Navbar

```html
<nav class="navbar is-fixed-top is-light" role="navigation">
    <div class="navbar-brand">
      <a class="navbar-item" href="#">
        <span class="icon">
          <i class="fa fa-user"></i>
        </span>
        <span>Contacts</span>
      </a>
    </div>
  </nav>
```
### Layout
```html
<div class="container is-fluid">
    <div class="columns">
      <contact-list class="column is-one-third"></contact-list>
      <router-view class="column"></router-view>
    </div>
  </div>
``` 
## Contact List

```html
<div class="panel">
  <div class="contact-list menu">
    <ul class="menu-list">
      <li repeat.for="contact of contacts">
        <a route-href="route: contacts; params.bind: {id:contact.id}" click.delegate="$parent.select(contact)" class="${contact.id === $parent.selectedId ? 'is-active' : ''}">
          <h4>${contact.firstName} ${contact.lastName}</h4>
          <p>${contact.email}</p>
        </a>
      </li>
    </ul>
  </div>
</div>
```

## Contact Detail

```html
<div class="panel">
    <div class="panel-heading">
      <h3>Profile</h3>
    </div>
    <div class="panel-block">
      <form role="form" style="width:100%">
        <div class="field columns">
          <label class="label column is-one-third">First Name</label>
          <div class="control column">
            <input type="text" placeholder="first name" class="input" value.bind="contact.firstName">
          </div>
        </div>
        ...
      </form>
  </div>
</div>
```
