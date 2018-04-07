# Aurelia Contact Manager Tutorial

This repo contains an implementation of the [Aurelia Framework Contact Manager Tutorial](http://aurelia.io/docs/tutorials/creating-a-contact-manager) using [Foundation for Sites](https://foundation.zurb.com/sites/docs/)
for the css.

## Foundation for Sites
The finished application...
![The Finished Product](contact-manager-foundation.png)


### Install Bulma

```
yarn add foundation-sites
``` 

or 

```
npm install foundation-sites
```

### Import into Main.ts
```typescript 
import 'foundation-sites/dist/css/foundation.css';
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

### Top Bar

```html
<nav class="top-bar" role="navigation">
  <div class="top-bar-left">
    <a class="" href="#">
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
<div class="grid-container">
  <div class="grid-x grid-margin-x">
    <contact-list class="cell small-4"></contact-list>
    <router-view class="cell small-8"></router-view>
  </div>
</div>
``` 
## Contact List

```html
<div class="card">
  <div class="card-section">
    <ul class="vertical menu">
      <li repeat.for="contact of contacts" class="${contact.id === $parent.selectedId ? 'is-active' : ''}">
        <a route-href="route: contacts; params.bind: {id:contact.id}" click.delegate="$parent.select(contact)">
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
<div class="card">
  <div class="card-divider">
    <h3>Profile</h3>
  </div>
  <div class="card-section">
    <form role="form">
      <div class="grid-x grid-padding-x">
        <div class="small-3 cell">
          <label>First Name</label>
        </div>
        <div class="small-9 cell">
          <input type="text" placeholder="first name" class="input" value.bind="contact.firstName">
        </div>
      </div>
    </form>
  </div>
</div>
```
