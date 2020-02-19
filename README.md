# Tips

## METEOR command line

- to create to full project recommended structure (from METEOR version 1.x ?) : `meteor create myProject --full`

- to create a specific METEOR version project : `meteor create --release X.Y.Z some-app-name`

## [FLOW-ROUTER](https://github.com/kadirahq/flow-router#api)

`FlowRouter.getRouteName()` gets the name of the route

`FlowRouter.getParam(paramName)` returns the value of a single URL parameter

`FlowRouter.getQueryParam(paramName)` returns the value of a single URL query parameter

- to create a path : `FlowRouter.path(pathDef, params, queryParams);`

## [zimme:active-route](https://github.com/meteor-activeroute/legacy)


## IRON-ROUTER migration

        meteor remove iron:router
        meteor add kadira:flow-router
        meteor add kadira:blaze-layout
        meteor add zimme:active-route

Find where `Router` is used.

`cklient/route.js` replacement

Delete /client/routerHooks.js, template/router/RouterLayoutApplication.html

/template/routerna.js modifications : activeIfRouteIs, activeIfRouteContains, activeIfAdminMenu

