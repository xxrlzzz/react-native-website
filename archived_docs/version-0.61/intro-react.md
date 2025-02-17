---
id: version-0.61-intro-react
title: React基础
description: To understand React Native fully, you need a solid foundation in React. This short introduction to React can help you get started or get refreshed.
original_id: intro-react
---

##### 本文档贡献者：[sunnylqm](https://github.com/search?q=sunnylqm%40qq.com+in%3Aemail&type=Users)(100.00%)

React Native runs on [React](https://reactjs.org/), a popular open source library for building user interfaces with JavaScript. To make the most of React Native, it helps to understand React itself. This section can get you started or can serve as a refresher course.

We’re going to cover the core concepts behind React:

- components
- JSX
- props
- state

If you want to dig deeper, we encourage you to check out [React’s official documentation](https://reactjs.org/docs/getting-started.html).

## Your first component

The rest of this introduction to React uses cats in its examples: friendly, approachable creatures that need names and a cafe to work in. Here is your very first Cat component:

<div class="toggler">
  <ul role="tablist" class="toggle-syntax">
    <li id="functional" class="button-functional" aria-selected="false" role="tab" tabindex="0" aria-controls="functionaltab" onclick="displayTabs('syntax', 'functional')">
      函数组件示例
    </li>
    <li id="classical" class="button-classical" aria-selected="false" role="tab" tabindex="0" aria-controls="classicaltab" onclick="displayTabs('syntax', 'classical')">
      Class组件示例
    </li>
  </ul>
</div>

<block class="functional syntax" />

```SnackPlayer name=Your%20Cat
import React from 'react';
import { Text } from 'react-native';
export default function Cat() {
  return (
    <Text>Hello, I am your cat!</Text>
  );
}
```

Here is how you do it: To define your `Cat` component, first use JavaScript’s [`import`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import) to import React and React Native’s [`Text`](text) Core Component:

```jsx
import React from 'react';
import { Text } from 'react-native';
```

Your component starts as a function:

```jsx
function Cat() {}
```

Whatever a function component returns is rendered as a React element. `Cat` will render a `<Text>` element:

```jsx
function Cat() {
  return <Text>Hello, I am your cat!</Text>;
}
```

You can export your function component with JavaScript’s [`export default`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export) for use throughout your app like so:

```jsx
export default function Cat() {
  return <Text>Hello, I am your cat!</Text>;
}
```

<block class="classical syntax" />

Class components tend to be a bit more verbose than function components.

```SnackPlayer name=Your%20Cat
import React, { Component } from 'react';
import { Text } from 'react-native';
export default class Cat extends Component {
  render() {
    return (
      <Text>Hello, I am your cat!</Text>
    );
  }
}
```

You additionally import `Component` from React:

```jsx
import React, { Component } from 'react';
```

Your component starts as a class extending `Component` instead of as a function:

```jsx
class Cat extends Component {}
```

Class components have a `render()` function. Whatever is returned inside it is rendered as a React element:

```jsx
class Cat extends Component {
  render() {
    return <Text>Hello, I am your cat!</Text>;
  }
}
```

And as with function components, you can export your class component:

```jsx
export default class Cat extends Component {
  render() {
    return <Text>Hello, I am your cat!</Text>;
  }
}
```

<block class="endBlock syntax" />

> This is one of many ways to export your component. This kind of export works well with the Snack Player. However, depending on your app’s file structure, you might need to use a different convention. This [handy cheatsheet on JavaScript imports and exports](https://medium.com/dailyjs/javascript-module-cheatsheet-7bd474f1d829) can help. Now take a closer look at that `return` statement. `<Text>Hello, I am your cat!</Text>` is using a kind of JavaScript syntax that makes writing elements convenient: JSX.

## JSX

React and React Native use **JSX,** a syntax that lets you write elements inside JavaScript like so: `<Text>Hello, I am your cat!</Text>`. The React docs have [a comprehensive guide to JSX](https://reactjs.org/docs/jsx-in-depth.html) you can reference to learn even more. Because JSX is JavaScript, you can use variables inside it. Here you are declaring a name for the cat, `name`, and embedding it with curly braces inside `<Text>`.

```SnackPlayer name=Curly%20Braces
import React from 'react';
import { Text } from 'react-native';
export default function Cat() {
  const name = "Maru";
  return (
    <Text>Hello, I am {name}!</Text>
  );
}
```

Any JavaScript expression will work between curly braces, including function calls like `{getFullName("Rum", Tum", "Tugger")}`:

```SnackPlayer name=Curly%20Braces
import React from 'react';
import { Text } from 'react-native';
export default function Cat() {
  function getFullName(firstName, secondName, thirdName) {
    return firstName + " " + secondName + " " + thirdName;
  }
  return (
    <Text>
      Hello, I am {getFullName("Rum", "Tum", "Tugger")}!
    </Text>
  );
}
```

You can think of curly braces as creating a portal into JS functionality in your JSX!

> Because JSX is included in the React library, it won’t work if you don’t have `import React from 'react'` at the top of your file!

## Custom Components

You’ve already met [React Native’s Core Components](intro-react-native-components). React lets you nest these components inside each other to create new components. These nestable, reusable components are at the heart of the React paradigm.

For example, you can nest [`Text`](text) and [`TextInput`](textinput) inside a [`View`](view) below, and React Native will render them together:

```SnackPlayer name=Custom%20Components
import React from 'react';
import { Text, TextInput, View } from 'react-native';
export default function Cat() {
  return (
    <View>
      <Text>Hello, I am...</Text>
      <TextInput
        style={{
          height: 40,
          borderColor: 'gray',
          borderWidth: 1
        }}
        defaultValue="Name me!"
      />
    </View>
  );
}
```

<div class="toggler">
  <span>Developer Notes</span>
  <span role="tablist" class="toggle-devNotes">
    <button role="tab" class="button-webNote" onclick="displayTabs('devNotes', 'webNote')">Web</button>
    <button role="tab" class="button-androidNote" onclick="displayTabs('devNotes', 'androidNote')">Android</button>
  </span>
</div>

<block class="webNote devNotes" />

> If you’re familiar with web development, `<View>` and `<Text>` might remind you of HTML! You can think of them as the `<div>` and `<p>` tags of application development. <block class="androidNote devNotes" />

> On Android, you usually put your views inside `LinearLayout`, `FrameLayout`, `RelativeLayout`, etc. to define how the view’s children will be arranged on the screen. In React Native, `View` uses Flexbox for its children’s layout. You can learn more in [our guide to layout with Flexbox](flexbox). <block class="endBlock devNotes" />

You can render this component multiple times and multiple places without repeating your code by using `<Cat>`:

```SnackPlayer name=Multiple%20Components
import React from 'react';
import { Text, TextInput, View } from 'react-native';
function Cat() {
  return (
    <View>
      <Text>I am a also cat!</Text>
    </View>
  );
}
export default function Cafe() {
  return (
    <View>
      <Text>Welcome!</Text>
      <Cat />
      <Cat />
      <Cat />
    </View>
  );
}
```

Any component that renders other components is a **parent component.** Here, `Cafe` is the parent component and each `Cat` is a **child component.**

You can put as many cats in your cafe as you like. Each `<Cat>` renders a unique element—which you can customize with props.

## Props

**Props** is short for “properties.” Props let you customize React components. For example, here you pass each `<Cat>` a different `name` for `Cat` to render:

```SnackPlayer name=Multiple%20Props
import React from 'react';
import { Text, View } from 'react-native';
function Cat(props) {
  return (
    <View>
      <Text>Hello, I am {props.name}!</Text>
    </View>
  );
}
export default function Cafe() {
  return (
    <View>
      <Cat name="Maru" />
      <Cat name="Jellylorum" />
      <Cat name="Spot" />
    </View>
  );
}
```

Most of React Native’s Core Components can be customized with props, too. For example, when using [`Image`](image), you pass it a prop named [`source`](image#source) to define what image it shows:

```SnackPlayer name=Props
import React from 'react';
import { Text, View, Image } from 'react-native';
export default function CatApp() {
  return (
    <View>
      <Image
        source="https://facebook.github.io/react-native/docs/assets/p_cat1.png"
        style={{width: 200, height: 200}}
      />
      <Text>Hello, I am your cat!</Text>
    </View>
  );
}
```

`Image` has [many different props](image#props), including [`style`](image#style), which accepts a JS object of design and layout related property-value pairs.

> Notice the double curly braces `{{ }}` surrounding `style`‘s width and height. In JSX, JavaScript values are referenced with `{}`. This is handy if you are passing something other than a string as props, like an array or number: `<Cat food={["fish", "kibble"]} /> age={2}`. However, JS objects are **_also_** denoted with curly braces: `{width: 200, height: 200}`. Therefore, to pass a JS object in JSX, you must wrap the object in **another pair** of curly braces: `{{width: 200, height: 200}}` You can build many things with props and the Core Components [`Text`](text), [`Image`](image), and [`View`](view)! But to build something interactive, you’ll need state.

## State

While you can think of props as arguments you use to configure how components render, **state** is like a component’s personal data storage. Sate is useful for handling data that changes over time or that comes from user interaction. State gives your components memory!

> As a general rule, use props to configure a component when it renders. Use state to keep track of any component data that you expect to change over time. The following example takes place in a cat cafe where two hungry cats are waiting to be fed. Their hunger, which we expect to change over time (unlike their names), is stored as state. To feed the cats, press their buttons—which will update their state.

<div class="toggler">
  <ul role="tablist" class="toggle-syntax">
    <li id="functional" class="button-functional" aria-selected="false" role="tab" tabindex="0" aria-controls="functionaltab" onclick="displayTabs('syntax', 'functional')">
      State with Function Components
    </li>
    <li id="classical" class="button-classical" aria-selected="false" role="tab" tabindex="0" aria-controls="classicaltab" onclick="displayTabs('syntax', 'classical')">
      State with Class Components
    </li>
  </ul>
</div>

<block class="functional syntax" />

You can add state to a component by calling [React’s `useState` Hook](https://reactjs.org/docs/hooks-state.html). A Hook is a kind of function that lets you “hook into” React features. For example, `useState` is a Hook that lets you add state to function components. You can learn more about [other kinds of Hooks in the React documentation.](https://reactjs.org/docs/hooks-intro.html)

```SnackPlayer name=State
import React, { useState } from "react";
import { Button, Text, View } from "react-native";
function Cat(props) {
  const [isHungry, setIsHungry] = useState(true);
  return (
    <View>
      <Text>
        I am {props.name}, and I am {isHungry ? "hungry" : "full"}!
      </Text>
      <Button
        onPress={() => {
          setIsHungry(false);
        }}
        disabled={!isHungry}
        title={isHungry ? "Pour me some milk, please!" : "Thank you!"}
      />
    </View>
  );
}
export default function Cafe() {
  return (
    <>
      <Cat name="Munkustrap" />
      <Cat name="Spot" />
    </>
  );
}
```

First, you will want to import `useState` from React like so:

```jsx
import React, { useState } from 'react';
```

Then you declare the component’s state by calling `useState` inside its function. In this example, `useState` creates an `isHungry` state variable:

```jsx
function Cat(props) {
  const [isHungry, setIsHungry] = useState(true);
  // ...
}
```

> You can use `useState` to track any kind of data: strings, numbers, Booleans, arrays, objects. For example, you can track the number of times a cat has been petted with `const [timesPetted, setTimesPetted] = useState(0)`! Calling `useState` does two things:

- it creates a “state variable” with an initial value—in this case the state variable is `isHungry` and its initial value is `true`
- it creates a function to set that state variable’s value—`setIsHungry`

It doesn’t matter what names you use. But it can be handy to think of the pattern as `[<getter>, <setter>] = useState(<initialValue>)`.

Next you add the [`Button`](button) Core Component and give it an `onPress` prop:

```jsx
<Button
  onPress={() => {
    setIsHungry(false);
  }}
  //..
/>
```

Now, when someone presses the button, `onPress` will fire, calling the `setIsHungry(false)`. This sets the state variable `isHungry` to `false`. When `isHungry` is false, the `Button`’s `disabled` prop is set to `true` and its `title` also changes:

```jsx
<Button
  //..
  disabled={!isHungry}
  title={isHungry ? 'Pour me some milk, please!' : 'Thank you!'}
/>
```

> You might’ve noticed that although `isHungry` is a [const](https://developer.mozilla.org/Web/JavaScript/Reference/Statements/const), it is seemingly reassignable! What is happening is when a state-setting function like `setIsHungry` is called, its component will re-render. In this case the `Cat` function will run again—and this time, `useState` will give us the next value of `isHungry`. Finally, put your cats inside a `Cafe` component:

```jsx
export default function Cafe() {
  return (
    <>
      <Cat name="Munkustrap" />
      <Cat name="Spot" />
    </>
  );
}
```

<block class="classical syntax" />

The older class components approach is a little different when it comes to state.

```SnackPlayer name=State%20and%20Class%20Components
import React, { Component } from "react";
import { Button, Text, View } from "react-native";
export class Cat extends Component {
  state = { isHungry: true };
  render(props) {
    return (
      <View>
        <Text>
          I am {this.props.name}, and I am
          {this.state.isHungry ? " hungry" : " full"}!
        </Text>
        <Button
          onPress={() => {
            this.setState({ isHungry: false });
          }}
          disabled={!this.state.isHungry}
          title={
            this.state.isHungry ? "Pour me some milk, please!" : "Thank you!"
          }
        />
      </View>
    );
  }
}
export default class Cafe extends Component {
  render() {
    return (
      <>
        <Cat name="Munkustrap" />
        <Cat name="Spot" />
      </>
    );
  }
}
```

As always with class components, you must import the `Component` class from React:

```jsx
import React, { Component } from 'react';
```

In class components, state is stored in a state object:

```jsx
export class Cat extends Component {
  state = { isHungry: true };
  //..
}
```

As with accessing props with `this.props`, you access this object inside your component with `this.state`:

```jsx
<Text>
  I am {this.props.name}, and I am
  {this.state.isHungry ? ' hungry' : ' full'}!
</Text>
```

And you set individual values inside the state object by passing an object with the key value pair for state and its new value to `this.setState()`:

```jsx
<Button
  onPress={() => {
    this.setState({ isHungry: false });
  }}
  // ..
</Button>
```

> Do not change your component's state directly by assigning it a new value with `this.state.hunger = false`. Calling `this.setState()` allows React to track changes made to state that trigger rerendering. Setting state directly can break your app's reactivity! When `this.state.isHungry` is false, the `Button`’s `disabled` prop is set to `false` and its `title` also changes:

```jsx
<Button
  // ..
  disabled={!this.state.isHungry}
  title={
    this.state.isHungry
      ? 'Pour me some milk, please!'
      : 'Thank you!'
  }
/>
```

Finally, put your cats inside a `Cafe` component:

```jsx
export default class Cafe extends Component {
  render() {
    return (
      <>
        <Cat name="Munkustrap" />
        <Cat name="Spot" />
      </>
    );
  }
}
```

<block class="endBlock syntax" />

> See the `<>` and `</>` above? These bits of JSX are [fragments](https://reactjs.org/docs/fragments.html). Adjacent JSX elements must be wrapped in an enclosing tag. Fragments let you do that without nesting an extra, unnecessary wrapping element like `View`.

---

Now that you’ve covered both React and React Native’s Core Components, let’s dive deeper on some of these core components by looking at [handling `<TextInput>`](handling-text-input).
