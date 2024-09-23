# @herdwatch-apps/ngx-intercom

[![npm](https://img.shields.io/npm/v/@herdwatch-apps/ngx-intercom.svg)](https://www.npmjs.com/package/@herdwatch-apps/ngx-intercom)
[![npm](https://img.shields.io/npm/dm/@herdwatch-apps/ngx-intercom.svg)](https://www.npmjs.com/@herdwatch-apps/ngx-intercom)

[//]: # ([![Build status][ci-image]][ci-url])
[![Maintenance](https://img.shields.io/maintenance/yes/2022.svg)]()

This is an Intercom wrapper for Angular 2+ which supports AoT and SSR.

It intends to support all documented intercom methods and PRs for functionality is greatly appreciated.

### STABLE VERSION

`master` is now hosting the latest stable version of `@herdwatch-apps/ngx-intercom`.

If you find issues with this version, please file an issue as soon as possible so we can take a look at it. We appreciate your cooperation!

### Installation

This package is on NPM, so just run
 ```sh
$ npm install @herdwatch-apps/ngx-intercom@latest
 ```

### Configuration

1. Import `IntercomModule` to `app.module.ts`. The module will automatically include the APP_ID instantiation, so you DO NOT need to copy the install script from Intercom and place it in your `index.html`.

```ts
import { IntercomModule } from '@herdwatch-apps/ngx-intercom';

@NgModule({
  imports: [
    ...
    IntercomModule.forRoot({
      appId: <your_app_id>, // from your Intercom config
      updateOnRouterChange: true // will automatically run `update` on router event changes. Default: `false`
    })
    ...
  ]
})
export class AppModule { }
```

2. Use in your components/directives/whatever you want!

```ts
// App
import { Component, OnInit } from '@angular/core';
import { Intercom } from '@herdwatch-apps/ngx-intercom';

@Component({
  selector: 'app',
  template: `...`
})
export class AppComponent implements OnInit {
  constructor(
    public intercom: Intercom
  ){}

  ngOnInit() {
    this.intercom.boot({
      app_id: <app_id>, // Please, pass your APP_ID here in case you don't use IntercomConfig
      // Supports all optional configuration.
      widget: {
        "activator": "#intercom" 
      }
    });
  }
}
```

### Development
To run live testing: `ng test`

To run tests: `npm test`

To run distribution: `npm run build:dist`

To publish `npm run build:dist && npm publish ./dist`


### Credits
Maintained by [Scott Wyatt](https://github.com/scott-wyatt) and [Wilson Hobbs](https://www.twitter.com/wbhob) in 2017 with contributions from [Florian Reifschneider](https://github.com/flore2003), [Devon Sams](https://www.twitter.com/POS1TRON), [Humberto Rocha](https://github.com/humrochagf), and [Luca GOUTY](http://luca.gouty.fr)


[ci-image]: https://img.shields.io/circleci/project/github/CaliStyle/@herdwatch-apps/ngx-intercom/master.svg

[//]: # ([ci-url]: https://circleci.com/gh/CaliStyle/@herdwatch-apps/ngx-intercom/tree/master)
