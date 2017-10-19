# nanographql [![stability][0]][1]
[![npm version][2]][3] [![build status][4]][5]
[![downloads][8]][9] [![js-standard-style][10]][11]

Tiny graphQL client library

## Usage
```js
var gql = require('nanographql')
var xhr = require('xhr')

var query = gql`
  query($number_of_repos:Int!) {
    viewer {
      name
      repositories(last: $number_of_repos) {
        nodes {
          name
        }
      }
    }
  }
`

var variables = { number_of_repos: 3 }
xhr('/query', { json: query(variables) }, function (err, res, body) {
  if (err) throw err
  if (body.errors) throw body.errors
  console.log(body.data)
})
```

## API
### `query = gql(string)`
Create a new graphql query function.

### `data = query([data])`
Create a new query object that can be sent as `application/json` to a server.

## License
[MIT](https://tldrlegal.com/license/mit-license)

[0]: https://img.shields.io/badge/stability-experimental-orange.svg?style=flat-square
[1]: https://nodejs.org/api/documentation.html#documentation_stability_index
[2]: https://img.shields.io/npm/v/nanographql.svg?style=flat-square
[3]: https://npmjs.org/package/nanographql
[4]: https://img.shields.io/travis/yoshuawuyts/nanographql/master.svg?style=flat-square
[5]: https://travis-ci.org/yoshuawuyts/nanographql
[6]: https://img.shields.io/codecov/c/github/yoshuawuyts/nanographql/master.svg?style=flat-square
[7]: https://codecov.io/github/yoshuawuyts/nanographql
[8]: http://img.shields.io/npm/dm/nanographql.svg?style=flat-square
[9]: https://npmjs.org/package/nanographql
[10]: https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat-square
[11]: https://github.com/feross/standard
