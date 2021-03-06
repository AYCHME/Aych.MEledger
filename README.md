# UAL for Ledger Authenticator

*NOTE: Currently does not work in Chromium/Chrome due to a known U2F bug https://github.com/LedgerHQ/ledgerjs/issues/306*

This authenticator is meant to be used with [Ledger](https://www.ledger.com/) and [Universal Authenticator Library](https://github.com/EOSIO/universal-authenticator-library). When used in combination with them, it gives developers the ability to request transaction signatures through a Ledger device using the common UAL API.

![EOSIO Labs](https://img.shields.io/badge/EOSIO-Labs-5cb3ff.svg)

# About EOSIO Labs

EOSIO Labs repositories are experimental.  Developers in the community are encouraged to use EOSIO Labs repositories as the basis for code and concepts to incorporate into their applications. Community members are also welcome to contribute and further develop these repositories. Since these repositories are not supported by Block.one, we may not provide responses to issue reports, pull requests, updates to functionality, or other requests from the community, and we encourage the community to take responsibility for these.

## Supported Environments
- The Ledger Authenticator will only work with Desktop Browser Environments from sites with SSL (https) encryption

## Getting Started

```bash
# Using yarn
yarn add ual-ledger

# Using npm
npm install ual-ledger --save
```

#### Dependencies

* You must have the [eos app](https://support.ledger.com/hc/en-us/articles/360008913653) installed on your ledger device. You can download it to your device using [Ledger Live](https://www.ledger.com/pages/ledger-live), if you do not already have it.
* Use one of the UAL renderers below.

  * React - `ual-reactjs-renderer`

  * PlainJS - `ual-plainjs-renderer`

* An `HTTPS` connection is required

* Enable `Arbitrary Data` in the settings of your eos app

#### Basic Usage with React

```jsx
import { Ledger } from 'ual-ledger'
import { UALProvider, withUAL } from 'ual-reactjs-renderer'

const exampleNet = {
  chainId: '',
  rpcEndpoints: [{
    protocol: '',
    host: '',
    port: '',
  }]
}

const App = (props) => (
  <div>{JSON.stringify(props.ual)}</div>
)

const AppWithUAL = withUAL(App)

const ledger = new Ledger([exampleNet])

<UALProvider chains={[exampleNet]} authenticators={[ledger]}>
  <AppWithUAL />
</UALProvider>
```

## Known Limitations
* The eos app installed on your ledger device can only deserialize the data of certain actions. If you submit an unknown action, the ledger will only display the contract, action, and a hex string of the data. You can view the eos app here https://github.com/LedgerHQ/ledger-app-eos/.
* This libary has only been tested with the `Ledger Nano S`. 


## Contribution
Check out the [Contributing](./CONTRIBUTING.md) guide and please adhere to the [Code of Conduct](./CONTRIBUTING.md#Conduct)

## License
[MIT licensed](./LICENSE)

## Important

See LICENSE for copyright and license terms.  Block.one makes its contribution on a voluntary basis as a member of the EOSIO community and is not responsible for ensuring the overall performance of the software or any related applications.  We make no representation, warranty, guarantee or undertaking in respect of the software or any related documentation, whether expressed or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose and noninfringement. In no event shall we be liable for any claim, damages or other liability, whether in an action of contract, tort or otherwise, arising from, out of or in connection with the software or documentation or the use or other dealings in the software or documentation. Any test results or performance figures are indicative and will not reflect performance under all conditions.  Any reference to any third party or third-party product, service or other resource is not an endorsement or recommendation by Block.one.  We are not responsible, and disclaim any and all responsibility and liability, for your use of or reliance on any of these resources. Third-party resources may be updated, changed or terminated at any time, so the information here may be out of date or inaccurate.  Any person using or offering this software in connection with providing software, goods or services to third parties shall advise such third parties of these license terms, disclaimers and exclusions of liability.  Block.one, EOSIO, EOSIO Labs, EOS, the heptahedron and associated logos are trademarks of Block.one.

Wallets and related components are complex software that require the highest levels of security.  If incorrectly built or used, they may compromise users’ private keys and digital assets. Wallet applications and related components should undergo thorough security evaluations before being used.  Only experienced developers should work with this software.
