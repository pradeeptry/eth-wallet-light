# eth-wallet-light

Sample code:

```javascript
const ethWalletLight = require('ethWalletLight')

var msgHash = "0x9c22ff5f21f0b81b113e63f7db6da94fedef11b2119b4088b89664fb9a3cb658"
var password = "mypassword"
var entropy = "2o3uhrb2i3pbrq32b"

// initialize
var keystore = new ethWalletLight.Keystore()
keystore.initialize(entropy, password)

// sign message
var signature = ethWalletLight.concatSignature(keystore.signMessageHash(msgHash, password))

// serialize to string
var serialized = keystore.serialize()

// recover from serialized
var keystore2 = new ethWalletLight.Keystore()
keystore2.fromSerialized(serialized)

// sign message
var signature2 = ethWalletLight.concatSignature(keystore2.signMessageHash(msgHash, password))

// get keystore variables
var address = keystore.address
var privateKey = keystore.getPrivateKey(password)
var mnemonic = keystore.getMnemonic(password)
```
