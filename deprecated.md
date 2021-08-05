# Stuff that need updating

## Deprecation

```sh
$ npm ci
npm WARN deprecated request-promise-native@1.0.9: request-promise-native has been deprecated because it extends the now deprecated request package, see https://github.com/request/request/issues/3142
npm WARN deprecated urix@0.1.0: Please see https://github.com/lydell/urix#deprecated
npm WARN deprecated mkdirp@0.5.4: Legacy versions of mkdirp are no longer supported. Please update to mkdirp 1.x. (Note that the API surface has changed to use Promises in 1.x.)
npm WARN deprecated har-validator@5.1.5: this library is no longer supported
npm WARN deprecated resolve-url@0.2.1: https://github.com/lydell/resolve-url#deprecated
npm WARN deprecated left-pad@1.3.0: use String.prototype.padStart()
npm WARN deprecated sane@4.1.0: some dependency vulnerabilities fixed, support for node < 10 dropped, and newer ECMAScript syntax/features added
npm WARN deprecated debug@3.2.6: Debug versions >=3.2.0 <3.2.7 || >=4 <4.3.1 have a low-severity ReDos regression when used in a Node.js environment. It is recommended you upgrade to 3.2.7 or 4.3.1. (https://github.com/visionmedia/debug/issues/797)
npm WARN deprecated uuid@3.4.0: Please upgrade  to version 7 or higher.  Older versions may use Math.random() in certain circumstances, which is known to be problematic.  See https://v8.dev/blog/math-random for details.
npm WARN deprecated request@2.88.2: request has been deprecated, see https://github.com/request/request/issues/3142
npm WARN deprecated @babel/polyfill@7.12.1:  This package has been deprecated in favor of separate inclusion of a polyfill and regenerator-runtime (when needed). See the @babel/polyfill docs (https://babeljs.io/docs/en/babel-polyfill) for more information.
npm WARN deprecated core-js@2.6.12: core-js@<3.3 is no longer maintained and not recommended for usage due to the number of issues. Because of the V8 engine whims, feature detection in old core-js versions could cause a slowdown up to 100x even if nothing is polyfilled. Please, upgrade your dependencies to the actual version of core-js.
```

## Outdated versions

```sh
$ npm outdated
Package                 Current  Wanted   Latest  Location                             Depended by
@babel/core              7.14.8  7.15.0   7.15.0  node_modules/@babel/core             codesandbox-ecommerce-shop
@babel/preset-env        7.14.9  7.15.0   7.15.0  node_modules/@babel/preset-env       codesandbox-ecommerce-shop
@sendgrid/mail            6.5.5   6.5.5    7.4.5  node_modules/@sendgrid/mail          codesandbox-ecommerce-shop
babel-jest               24.9.0  24.9.0   27.0.6  node_modules/babel-jest              codesandbox-ecommerce-shop
dotenv                    7.0.0   7.0.0   10.0.0  node_modules/dotenv                  codesandbox-ecommerce-shop
eslint                   5.16.0  5.16.0   7.32.0  node_modules/eslint                  codesandbox-ecommerce-shop
eslint-config-airbnb     17.1.1  17.1.1   18.2.1  node_modules/eslint-config-airbnb    codesandbox-ecommerce-shop
eslint-config-prettier    4.3.0   4.3.0    8.3.0  node_modules/eslint-config-prettier  codesandbox-ecommerce-shop
express-validator         5.3.1   5.3.1   6.12.1  node_modules/express-validator       codesandbox-ecommerce-shop
express-winston           3.4.0   3.4.0    4.1.0  node_modules/express-winston         codesandbox-ecommerce-shop
helmet                   3.23.3  3.23.3    4.6.0  node_modules/helmet                  codesandbox-ecommerce-shop
jest                     24.9.0  24.9.0   27.0.6  node_modules/jest                    codesandbox-ecommerce-shop
mocha                     6.2.3   6.2.3    9.0.3  node_modules/mocha                   codesandbox-ecommerce-shop
mysql2                    1.7.0   1.7.0    2.2.5  node_modules/mysql2                  codesandbox-ecommerce-shop
prettier                 1.19.1  1.19.1    2.3.2  node_modules/prettier                codesandbox-ecommerce-shop
sequelize                5.22.4  5.22.4    6.6.5  node_modules/sequelize               codesandbox-ecommerce-shop
sequelize-cli             5.5.1   5.5.1    6.2.0  node_modules/sequelize-cli           codesandbox-ecommerce-shop
stripe                   6.36.0  6.36.0  8.168.0  node_modules/stripe                  codesandbox-ecommerce-shop
supertest                 4.0.2   4.0.2    6.1.4  node_modules/supertest               codesandbox-ecommerce-shop
```
