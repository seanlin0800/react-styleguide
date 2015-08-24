# React 風格指南 (ES5)

## 目錄

## 基本規則
 - **JavaScript**: 基本上遵守 [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript/tree/master/es5)。原則上 Airbnb 的規則和大多數開發者慣用規則是一樣的，需要注意的有:
   - [不用 Single Var Pattern](https://github.com/airbnb/javascript/tree/master/es5#variables)
   - anonymous function expressions 左小括號前沒有空白，和 [大師 Crockford](http://javascript.crockford.com/code.html) 建議的不同
``` javascript
// bad
var anonymous = function () {
  return true;
};

// good
var anonymous = function() {
  return true;
};
```
 - 一個 module 只宣告一個 React component
 - 原則上使用 JSX 語法，別用 `React.createElement`

## 命名
 - **附檔名**: 對 React components 使用 `.jsx`
 - **檔名**: 使用PascalCase ，例如: `ReservationCard.jsx`
 - **變數命名**: 
   - React components -> PascalCase
   - instances -> camelCase 其實就跟一般 local 變數命名一樣
   - prop names -> camelCase

範例:
``` javascript
// bad
var reservationCard = require('./ReservationCard');

// good
var ReservationCard = require('./ReservationCard');

// bad
var ReservationItem = <ReservationCard />;

// good
var reservationItem = <ReservationCard />;

// bad
<Foo
  UserName="hello"
  phone_number={12345678}
/>

// good
<Foo
  userName="hello"
  phoneNumber={12345678}
/>
```

## 引號
對 JSX attributes 使用雙引號，而其餘字串就如同一般 js 慣例使用單引號
``` javascript
// bad
<Foo className='bar' />

// good
<Foo className="bar" />

// bad
<Foo style={{ left: "20px" }} />

// good
<Foo style={{ left: '20px' }} />
```

## 排版
如果 props 太多或太長的話，必須拆成多行，每個 prop 以及 closing tag 必須獨立一行，如此一來不僅可讀性較高， props 變動時也很方便修改。

範例:
``` javascript
// bad
<Foo superLongParam="bar"
     anotherSuperLongParam="baz" />

// good
<Foo
  superLongParam="bar"
  anotherSuperLongParam="baz"
/>

// 如果 props 放得下的話，可以在同一行
<Foo bar="bar" />

// 正常縮排 children
<Foo
  superLongParam="bar"
  anotherSuperLongParam="baz"
>
  <Spazz />
</Foo>
```

如果一個含有 JSX tags 的 statement 有多行的話，必須加上小括號:
``` javascript
/// bad
return <MyComponent className="long body" foo="bar">
         <MyChild />
       </MyComponent>;

// good
return (
  <MyComponent className="long body" foo="bar">
    <MyChild />
  </MyComponent>
);

// good, when single line
var body = <div>hello</div>;
return <MyComponent>{body}</MyComponent>;
```

為了提高程式的可讀性， React.createClass() 傳入的 object 前後須有空白行:
``` javascript
// bad
var Foo = React.createClass({
  render: function() {
    return (
      <div className="bar">
        <Bar />
      </div>
    );
  }
});

// good
var Foo = React.createClass({

  render: function() {
    return (
      <div className="bar">
        <Bar />
      </div>
    );
  }

});
```

## JSX Tags
沒有 chidren 的話必須使用 self-closing tag
``` javascript
// bad
<Foo className="stuff"></Foo>

// good
<Foo className="stuff" />
```

self-closing tag 前面必須有**一個**空格
``` javascript
// bad
<Foo/>

// very bad
<Foo                 />

// bad
<Foo
 />

// good
<Foo />
```

## propTypes
React components 一定要設定 propTypes。

如此一來確保參數合法性(在 development mode 才會檢查)，也讓使用的人明白如何正確使用該 component。

``` javascript
// bad
var Foo = React.createClass({

  render : function() {
    return <div />;
  };
 
});

// good
var Foo = React.createClass({

  propTypes: {
    optionalArray: React.PropTypes.array,
    optionalString: React.PropTypes.string
  },

  render : function() {
    return <div />;
  };

});
```

## Method 順序
lifecycle methods : 由上而下， 依執行順序排序
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

範例:
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

## 參考資料
 - https://github.com/airbnb/javascript/tree/master/react
 - http://reactjsnews.com/react-style-guide-patterns-i-like/
 - http://web-design-weekly.com/2015/01/29/opinionated-guide-react-js-best-practices-conventions/
 - http://aeflash.com/2015-02/react-tips-and-best-practices.html

