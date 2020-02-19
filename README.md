# Tips

## METEOR command line

From METEOR version 1.x ? `meteor create myProject --full` to create to full project recommended structure.

## FLOW-ROUTER

`FlowRouter.getRouteName()` gets the name of the route
`FlowRouter.getParam(paramName)` returns the value of a single URL parameter
`FlowRouter.getQueryParam(paramName)` returns the value of a single URL query parameter



## IRON-ROUTER migration

        meteor remove iron:router
        meteor add kadira:flow-router
        meteor add kadira:blaze-layout

Find where `Router` is used.

`cklient/route.js` replacement

Delete /client/routerHooks.js, template/router/RouterLayoutApplication.html

/template/routerna.js modifications : activeIfRouteIs, activeIfRouteContains, activeIfAdminMenu
