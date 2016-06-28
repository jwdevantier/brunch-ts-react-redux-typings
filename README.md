# brunch-typed-redux

A brunch skeleton for a React/Redux application written in Typescript.

Based on [brunch-typed-redux](https://github.com/ThinTim/brunch-typed-redux)
Based on [with-redux](https://github.com/brunch/with-redux) and [ng2-brunch](https://github.com/colinbate/ng2-brunch).

## Get started


```bash
#Install typescript
npm install -g typescript typings

#Install dependencies
npm install

#Install type definitions
#See known bugs below if experiencing issues with the 'connect' function from react-redux
tsd install

#Start a local dev server
npm run start
```

## Known bugs

### Bad type definition for `connect`

At the time of writing, the typescript definition for react-redux does not allow stateless components to be wrapped using the `connect` function. Until the definitions are corrected, this can be fixed by changing

```
interface ComponentDecorator<TOriginalProps extends Props<any>, TOwnProps extends Props<any>> {
  (component: ComponentClass<TOriginalProps>): ComponentClass<TOwnProps>;
}
```

to this:

```
interface ComponentDecorator<TOriginalProps extends Props<any>, TOwnProps extends Props<any>> {
  (component: ComponentClass<TOriginalProps> | StatelessComponent<TOriginalProps>): ComponentClass<TOwnProps>;
}
```

## changelog
 * changed project to use 'typings' in favour of tsd which has become deprecated.
   - exact instructions followed: [How to upgrade from tsd to typings](http://ilikekillnerds.com/2016/01/how-to-upgrade-from-tsd-to-typings/)
