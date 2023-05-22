# Lifecycle Hooks

Every new component in an application goes through those lifecycle hooks ( stages ).

## Lifecycle hooks diagram
::: mermaid
  flowchart TD;
  id1( app = Vue.createApp 'options' / app.mount 'el' ) --> id2( init events & lifecycle );
  id2 --Hook: \before create\--> id3( init injections & reactivity );
  id3 --Hook: \created\ --> id4{ Has template };
  id4 --Yes--> id5( complete template into render function);
  id4 --No--> id6( complete el's inner HTML as template );
  id5 --Hook:--> id7( Create app.$el and replace 'el' with it );
  id6 --\beforeMonunt\--> id7( Create app.$el and replace 'el' with it );
  id7 --Hook: \Mounted\--> id8(( Mounted ));
  id8 -.when app.unmount function is called.-.Hook:beforeUnmounted.- id10(( Unmounted ));
  id8 -.Hook: \afterUpdate\.- id9( Virtual DOM re-rendered and patch );
  id8 -.when data change.-Hook:beforeUpdate.- id9;
  id10 -.- .Hook:unmounted


:::