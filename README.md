# Strapi plugin moesif

Plugin to add Moesif API Analytics and Monitoring to Strapi!
https://www.moesif.com/

## Installation
- Install the plugin
```
npm install strapi-plugin-moesif
```
- Add the following to ./config/middlewares.js
```
settings: {
  moesif: {
    enabled: true,
    debug: false,
    applicationId: env('MOESIF_APPLICATION_ID', ''),
    identifyUserL function (req, res) {
      if (req.state && req.state.user) {
        return req.state.user.id;
      }
      return undefined;
    },
    getSessionToken: function (req, res) {
      return req.headers['Authorization'];
    },
    disableBatching: false,
    logBody: true,
    callback: function (error, data) {
      console.log('Moesif error: ' + JSON.stringify(error));
    }
  }
}
```
- Add MOESIF_APPLICATION_ID to your environment variables

## Heroku
If using Heroku, simply install the Moesif application as an add-on. The MOESIF_APPLICATION_ID environment variable will be automatically created and managed by Heroku. 

