# think-pagination

pagination for ThinkJS 3, if you want to in ThinkJS 2.x, please view [README_V2](./README_V2.md)

## install

```sh
npm install think-pagination
```

## how to use

### controller

```js
const pagination = require('think-pagination');

module.exports = class extends think.Controller {
  async indexAction() {
    const data = await this.model('user').countSelect();
    const html = pagination(data, this.ctx, {});
    this.assign('pagination', html);
  }
}
```

### view

#### ejs

```html
{%-pagination%}
```

#### nunjucks

```html
{{pagination | safe}}
```

## API

### pagination(pagerData, ctx, options)

* `pagerData`  get from by model.countSelect
* `ctx` ctx object
* `options` options

`options`:

```js
{
  desc: false, //show description
    pageNum: 2, 
    url: '', //page url, when not set, it will auto generated
    class: '', //pagenation extra class
    text: {
      next: 'Next',
      prev: 'Prev',
      total: 'count: __COUNT__ , pages: __PAGE__'
    }
}
```
