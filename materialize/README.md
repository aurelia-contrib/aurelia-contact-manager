# Aurelia Contact Manager Tutorial

This repo contains an implementation of the [Aurelia Framework Contact Manager Tutorial](http://aurelia.io/docs/tutorials/creating-a-contact-manager) using the 
[Materialize Css Framework](http://materializecss.com/).

## Materialize

![The Finished Application](contact-manager-materialize.png)

## install Materialize

```
yarn add materialize-css@next
``` 

or 

```
npm install materialize-css@next
```

### Import into Main.ts
```typescript 
import 'materialize-css/dist/css/materialize.css';
```

## Google Material Icons

To use the Goolge Material icons in the app the add the following link to the index.ejs file.

```html
<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
```
## App Shell

## Navbar

```html
<div class="navbar-fixed">
  <nav role="navigation">
    <div class="nav-wrapper">
      <a class="brand-logo" href="#">
        <i class="material-icons">person</i>
        <span>Contacts</span>
      </a>
    </div>
  </nav>
</div>
```
### Layout

```html
<div>
  <div class="row">
    <contact-list class="col s4"></contact-list>
    <router-view class="col s8"></router-view>
  </div>
</div>
``` 
## Contact List 

```html
<div class="contact-list card">
  <div class="card-content">
    <div class="collection">
      <a repeat.for="contact of contacts" class="collection-item ${contact.id === $parent.selectedId ? 'active' : ''}"
          route-href="route: contacts; params.bind: {id:contact.id}" click.delegate="$parent.select(contact)" >
          <h4>${contact.firstName} ${contact.lastName}</h4>
          <p>${contact.email}</p>
      </a>
    </div>
  </div>
</div>
```

## Contact Detail

```html
<<div class="card">
  <div class="card-content">
    <div class="card-title">
      <h3>Profile</h3>
    </div>
    <div>
      <form role="form">
        <div class="row">
          <div class="input-field col s12">
            <input type="text" placeholder="first name" name="first-name" value.bind="contact.firstName">
            <label for="first-name">First Name</label>
          </div>
        </div>
        ...
      </form>
    </div>
  </div>
</div>
```
