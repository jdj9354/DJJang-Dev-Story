---
layout: post
title:  "React Update Child Property"
comments: true
categories: React
date:   2019-02-10 21:26:00 +0900
---

> ## Updating Child View with property

In react, in order to pass parameter to child Component, we set property value usually.
And Child component get property value from Parent in side **'constructor'** function.
Like,

```ES6
class Payment extends Component {
    constructor(props) {
        super(props);
        this.state = {
            totalPrice: props.totalPrice,
            itemsArray: props.itemsArray
        }
    }
```

But This is not enough. Because when there is change on property, Child doesn't updated automatically.
We can resolve this situation, by utilizing another callback function **'componentWillReceiveProps'**

```ES6
componentWillReceiveProps(nextProps, nextContext) {
        this.setState({
            totalPrice: nextProps.totalPrice,
            itemsArray: nextProps.itemsArray
        })
    }
```

With above callback function, when **'render'** function of parent view is called, **'componentWillReceiveProps'** , ''**render'** functions of child view is also called.