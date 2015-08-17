# React 風格指南

## Table of Contents

## Method Organization
  1. displayName
  1. propTypes
  1. contextTypes
  1. childContextTypes
  1. mixins
  1. statics
  1. defaultProps
  1. getDefaultProps
  1. getInitialState
  1. getChildContext
  1. componentWillMount
  1. componentDidMount
  1. componentWillReceiveProps
  1. shouldComponentUpdate
  1. componentWillUpdate
  1. componentDidUpdate
  1. componentWillUnmount
  1. event handlers, such as _handleXxx()
  1. "private" methods, such as _renerXxx() and _getXxx()
  1. render

``` javascript
React.createClass({
  displayName : '',
  propTypes: {},
  mixins : [],
  getInitialState : function() {},
  componentWillMount : function() {},
  componentWillUnmount : function() {},
  _handleChange : function() {},
  _renderItems : function() {},
  render : function() {}
});
```

## References
 - https://github.com/airbnb/javascript/tree/master/react
 - http://reactjsnews.com/react-style-guide-patterns-i-like/
 - http://web-design-weekly.com/2015/01/29/opinionated-guide-react-js-best-practices-conventions/
 - http://aeflash.com/2015-02/react-tips-and-best-practices.html
 - https://github.com/airbnb/javascript/tree/master/react

