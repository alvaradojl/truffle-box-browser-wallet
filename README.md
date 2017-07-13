I won't be maintaining this repo anymore because truffle box has published a react-redux truffle box. You should use that one.

https://github.com/truffle-box/react-auth-box

# Truffle Box (React, Redux and Authentication)

All truffle boxes come with Truffle, Webpack and React. This box adds react-router, redux and redux-auth-wrapper for authentication powered by a smart contract. Great for building your own auth system.

## Installation

1. Install truffle and an ethereum client. For local development, try EthereumJS TestRPC.
    ```javascript
    npm install -g truffle // Version 3.0.5+ required.
    npm install -g ethereumjs-testrpc
    ```

2. Clone or download the truffle box of your choice.
    ```javascript
    git clone [repo]
    ```

3. Install the node dependencies.
    ```javascript
    npm install
    ```

4. Compile and migrate the contracts.
    ```javascript
    truffle compile
    truffle migrate
    ```

5. Run the webpack server for front-end hot reloading. For now, smart contract changes must be manually recompiled and migrated.
    ```javascript
    npm run start
    ```

6. Jest is included for testing React components and Truffle's own suite is incldued for smart contracts. Be sure you've compile your contracts before running jest, or you'll receive some file not found errors.
    ```javascript
    // Runs Jest for component tests.
    npm run test

    // Runs Truffle's test suite for smart contract tests.
    truffle test
    ```

7. To build the application for production, use the build command. A production build will be in the build_webpack folder.
    ```javascript
    npm run build
    ```

## Passing web3 to components through the Redux store

1. Define web3 in your mapStateToProps function in your container component.
    ```
        const mapStateToProps = (state, ownProps) => {
      return {
        web3: state.web3
      }
    }
    ```

2. In your mapDispatchToProps of your container component, pass web3 into the function that you pass as a prop to your presentation component 
    ```
    const mapDispatchToProps = (dispatch) => {
      return {
        onSignUpFormSubmit: (name, web3) => {
          event.preventDefault();

          dispatch(signUpUser(name, web3))
        }
      }
    }
    ```

3. In the presentation component, set web3 in the state within the constructor function.


## FAQ

* __Why is there both a truffle.js file and a truffle-config.js file?__

    Truffle requires the truffle.js file be named truffle-config on Windows machines. Feel free to delete the file that doesn't correspond to your platform.

* __Where is my production build?__

    The production build will be in the build_webpack folder. This is because Truffle outputs contract compilations to the build folder.

* __Where can I find more documentation?__

    All truffle boxes are a marriage of [Truffle](http://truffleframework.com/) and a React setup created with [create-react-app](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md). Either one would be a great place to start!
