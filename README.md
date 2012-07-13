Backbone-ZombieNation
=====================

A small Backbone plugin which helps to manage bindings and subviews in a Backbone Application.

Usage
=====

There are two parts to the plugin: Event bindings, and Subviews. Both of these hook into the regular `Backbone.View.prototype.remove()` function, allowing events and child views to be automatically released from memory when the view is removed.

### Event Bindings

Use `bindTo` and `unbindFromAll` to handle bindings.

#### `bindTo(object, event, callback)`

Binds `event` to `object`. `object` must be an extension of `Backbone.Event`. When the `event` is triggered elsewhere, `callback` is called.

When this method is called, the binding is stored in an internal `bindings` array. This allows the event to be unbound later hrough a call to `unbindFromAll`.

#### `unbindFromAll()`

Called automatically when the View is `dispose`d. Can also be called at any time to unbind all events which were previously bound with `bindTo`.

### SubViews

Use `addChild` and `disposeChildren` to handle nested views.

#### `addChild`

Adds a child view to this parent view.

When this method is called, the child view is stored in an internal `children` array. This allows the event to be unbound later hrough a call to `disposeChildren`.

#### `disposeChildren`

Called automatically when the View is `dispose`d. Can also be called at any time to remove all children from the DOM which were previously added with `addChild`.

