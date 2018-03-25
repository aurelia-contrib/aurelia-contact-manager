# Aurelia Contact Manager Tutorial

This repo contains an implementation of the [Aurelia Framework Contact Manager Tutorial](http://aurelia.io/docs/tutorials/creating-a-contact-manager) using the 
[UIKit Css Framework](https://getuikit.com/docs/introduction)

## UIKit

The finished Appplication...
![the finished product](/contact-manager-uikit.png)
## Install UIKit

```
yarn add uikit
```

or

```
npm install uikit
```

## Configure UIKit

UIKit's css and javascript will need to be imported into main.ts, also to use the icons
included with  UIKit they will need to be configured as part of bootstrapping the application.
```typescript
import UIKit from 'uikit';
import Icons from 'uikit/dist/js/uikit-icons';

import 'uikit/dist/css/uikit.css';

...

aurelia.start().then(() => {
    aurelia.setRoot(PLATFORM.moduleName('app'))
    UIKit.use(Icons);
  });
```

## App Shell

### Navbar

```html
<div uk-sticky="sel-target: .uk-navbar-container; cls-active: uk-navbar-sticky">
    <nav class="uk-navbar-container" uk-navbar role="navigation">
      <div class="uk-navbar-left">
        <a class="uk-navbar-item uk-logo" href="#">
          <span uk-icon="icon: user"></span>
          <span>Contacts</span>
        </a>
      </div>
    </nav>
  </div>
```
### Layout

```html
<div class="uk-container uk-margin">
    <div class="uk-grid">
      <contact-list class="uk-width-1-3"></contact-list>
      <router-view class="uk-width-2-3"></router-view>
    </div>
  </div>
```
## Contact List

```html
<div class="uk-card uk-card-default">
    <div class="uk-card-body uk-padding-small">
      <ul class="uk-nav">
        <li repeat.for="contact of contacts" class="uk-padding-small ${contact.id === $parent.selectedId ? 'uk-active uk-background-primary uk-light' : ''}">
          <a route-href="route: contacts; params.bind: {id:contact.id}" click.delegate="$parent.select(contact)">
            <h4>${contact.firstName} ${contact.lastName}</h4>
            <div>${contact.email}</p>
          </a>
        </li>
      </ul>
    </div>
  </div>
```

## Contact Detail

```html
<div class="uk-card uk-card-default">
    <div class="uk-card-header uk-card-primary">
      <h3 class="uk-card-title">Profile</h3>
    </div>
    <div class="uk-card-body">
      <form class="uk-form-horizontal" role="form">
        <div>
          <label class="uk-form-label">First Name</label>
          <div class="uk-form-controls">
              <input type="text" placeholder="first name" class="uk-input" value.bind="contact.firstName">
          </div>
        </div>
        
        ...

        <div class="uk-margin">
          <button class="uk-button uk-button-primary uk-align-right" click.delegate="save()" disabled.bind="!canSave">Save</button>
        </div>
      </form>
  </div>
</div>
```
