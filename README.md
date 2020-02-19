# Tips

## METEOR command line

- to create to full project recommended structure (from METEOR version 1.x ?) : `meteor create myProject --full`

- to create a specific METEOR version project : `meteor create --release X.Y.Z some-app-name`

## [FLOW-ROUTER](https://github.com/kadirahq/flow-router#api)

`FlowRouter.getRouteName()` gets the name of the route

`FlowRouter.getParam(paramName)` returns the value of a single URL parameter

`FlowRouter.getQueryParam(paramName)` returns the value of a single URL query parameter

- to create a path : `FlowRouter.path(pathDef, params, queryParams);`

logging and authentication : https://medium.com/@satyavh/using-flow-router-for-authentication-ba7bb2644f42

### Subscriptions
#### Global

        FlowRouter.subscriptions = function() {
                this.register('myCourses', Meteor.subscribe('courses'));
        };
        
#### Associated with a route

        FlowRouter.route('/blog/:postId', {
                subscriptions: function(params, queryParams) {
                        this.register('myPost', Meteor.subscribe('blogPost', params.postId));
                }
        });

#### To check if subscriptions are loaded

After you've registered your subscriptions, you can reactively check for the status of those subscriptions like this:

        Tracker.autorun(function() {
                console.log("Is myPost ready?:", FlowRouter.subsReady("myPost"));
                console.log("Are all subscriptions ready?:", FlowRouter.subsReady());
        });

## [zimme:active-route](https://github.com/meteor-activeroute/legacy)

- to set `active` or `false` :

        <li class="{{isActivePath '/home'}}">...</li>
        <li class="{{isActivePath path='/home'}}">...</li>
        <li class="{{isActivePath regex='ajouter|autre'}}">...</li>    // if path contains `ajouter` ou `autre`
        <li class="dropdown {{isActivePath regex='^/ajouter'}}">      // Start with `/ajouter`
        <li class="dropdown {{isActivePath regex='/ajouter$'}}">      // End with `/ajouter`
 

## IRON-ROUTER migration

        meteor remove iron:router
        meteor add kadira:flow-router
        meteor add kadira:blaze-layout
        meteor add zimme:active-route

Find where `Router` is used.

`cklient/route.js` replacement

Delete /client/routerHooks.js, template/router/RouterLayoutApplication.html

/template/routerna.js modifications : supprimer helpers activeIfRouteIs, activeIfRouteContains, activeIfAdminMenu

remplacer activeIfRouteIs par isActivePath in routerNav.html et changer le nom de route par le path

remplacer par activeIfRouteContains {{isActivePath regex='$\\/ajouter'}}

