# Java SDK

SDK [download](https://github.com/okex/okchain-java-sdk)

## Obtain account information through a remote blockchain node
```java
public JSONObject getAccountFromNode(String userAddress) throws NullPointerException;
```
Enter parameters:

|Name|Type|Mark|
|---|---|---|
|userAddress|String|account address|

Results returned:
```json
{
	"type": "auth/Account",
	"value": {
		"address": "okchain1g7c3nvac7mjgn2m9mqllgat8wwd3aptdqket5k",
		"coins": [{
			"denom": "okt",
			"amount": "10000.00000000"
		}],
		"public_key": {
			"type": "tendermint/PubKeySecp256k1",
			"value": "Aga5P7TWoqq+6cmxOTHhj9tLqFlHNlLpWMEdAfHcokp+"
		},
		"account_number": "4",
		"sequence": "0"
	}
}
```

## Create a private key and generate a corresponding public key and address
```java
    public AddressInfo createAddressInfo();
```
Parameters entered: Null


Results returned:
```java
public class AddressInfo {
    private String privateKey;//Private key
    private String publicKey;//Public key
    private String userAddress;//Address
}
```
## Enter a private key to obtain a corresponding public key and address
```java
    public AddressInfo getAddressInfo(String privateKey) throws NullPointerException;
```
Enter paremeters:

|Name|Type|Mark|
|---|---|---|
|privateKey|String|private key|

Results returned:
```java
public class AccountInfo extends AddressInfo {
    private String accountNumber;//Account ID on OKChain
    private String sequenceNumber;//Corresponding serial number sent by the account next time
}
```
## Obtain account information through a private key
```java
    public AccountInfo getAccountInfo(String privateKey) throws NullPointerException;
```
Enter paremeters:

|Name|Type|Mark|
|---|---|---|
|privateKey|String|private key|

Results returned:Same as above
## Generate a private key through a mnemonic phrase
```java
    public String getPrivateKeyFromMnemonic(String mnemonic);
```
## Generate a new mnemonic phrase
```java
    public String generateMnemonic();
```
## Generate a KeyStore file in the current directory
```java
    public String generateKeyStore(String privateKey, String passWord) throws CipherException, IOException;
```
Enter paremeters:

|Name|Type|Mark|
|---|---|---|
|privateKey|String|private key|
|passWord|String|password|

Results returned:

|Name|Type|Mark|
|---|---|---|
|KeyStoreName|String|KeyStore file name|

## Restore a private key in a KeyStore file at a specific file path
```java
    public String getPrivateKeyFromKeyStore(String keyStoreFilePath, String passWord) throws IOException, CipherException;
```
Enter paremeters:

|Name|Type|Mark|
|---|---|---|
|keyStoreFilePath|String|KeyStore file path|
|passWord|String|password|

Results returned:

|Name|Type|Mark|
|---|---|---|
|privateKey|String|private key|

## Start a transfer transaction
```java
    public JSONObject sendSendTransaction(AccountInfo account, String to, List<Token> amount, String memo) throws NullPointerException, IOException;
```
Enter paremeters:

|Name|Type|Mark|
|---|---|---|
|account|AccountInfo|account information|
|to|String|recipient address|
|amount|Token[]|information on a cryptocurrency for transfer|
|memo|String|remarks|

```java
public class Token {
    private String amount;//The amount of the cryptocurrency must be rounded to the nearest 8 decimal places, eg. 1.00000000
    private String denom;//Cryptocurrency information, eg. OKT
}
```
Results returned:
```json
{
	"height": "0",
	"txhash": "A1F5688C769621E04FFF2617BD1C1931607FD3178368A362CEC8EFAD9D8FFB46"//Transaction hash
}
```
## Start a transaction
```java
    public JSONObject sendPlaceOrderTransaction(AccountInfo account, RequestPlaceOrderParams parms, String memo) throws NullPointerException, IOException;
```
Enter paremeters:

|Name|Type|Mark|
|---|---|---|
|account|AccountInfo|account information|
|price|String|amount of cryptocurrency rounded to the nearest 8 decimal places|
|product|String|pair, eg. acoin_okt|
|quantity|String|amount of cryptocurrency rounded to the nearest 8 decimal places|
|side|String|"BUY"or"SELL"|
|memo|String|remarks|

Results returned:
```json
{
	"height": "0",
	"txhash": "A1F5688C769621E04FFF2617BD1C1931607FD3178368A362CEC8EFAD9D8FFB46"//Transaction hash
}
```
## Cancel a transaction
```java
    public JSONObject sendCancelOrderTransaction(AccountInfo account, String orderId, String memo) throws NullPointerException, IOException;
```
Enter paremeters:

|Name|Type|Mark|
|---|---|---|
|account|AccountInfo|account information|
|orderId|String|order id|
|memo|String|remarks|

Results returned:
```json
{
	"height": "0",
	"txhash": "A1F5688C769621E04FFF2617BD1C1931607FD3178368A362CEC8EFAD9D8FFB46"//Transaction hash
}
```
## Start a multi-transfer transaction
```java
    public JSONObject sendMultiSendTransaction(AccountInfo account, List<TransferUnit> transfers, String memo) throws IOException;

```
Enter paremeters:

|Name|Type|Mark|
|---|---|---|
|account|AccountInfo|account information|
|transfers|TransferUnit[]|recipient information|
|memo|String|remarks|

```java
public class TransferUnit {
    private List<Token> coins;//Information on the cryptocurrency of the recipient
    private String to;//Recipient address
}
```

Results returned:
```json
{
	"height": "0",
	"txhash": "A1F5688C769621E04FFF2617BD1C1931607FD3178368A362CEC8EFAD9D8FFB46"//Transaction hash
}
```
## Obtain information of all cryptocurrencies of a user
```java
    public BaseModel getAccountALLTokens(String address, String show) throws NullPointerException;
```
Refer to http api description for parameters and return parameters

Results returned:

```java
public class BaseModel {
    private String code;
    private String data;
    private String msg;
    private String detailMsg;
}
```
## Obtain information on a single cryptocurrency of a user
```java
    public BaseModel getAccountToken(String address, String symbol) throws NullPointerException;
```
Refer to http api description for parameters and return parameters
## Obtain information on all cryptocurrencies
```java
    public BaseModel getTokens();
```
Refer to http api description for parameters and return parameters
## Obtain information on a single cryptocurrency
```java
    public BaseModel getToken(String symbol) throws NullPointerException;
```
Refer to http api description for parameters and return parameters
## Obtain information on all trading pairs
```java
    public BaseModel getProducts();
```
Refer to http api description for parameters and return parameters
## Obtain information on market depth
```java
    public BaseModel getDepthBook(String product) throws NullPointerException;
```
Refer to http api description for parameters and return parameters
## Obtain candlestick data
```java
    public BaseModel getCandles(String granularity, String instrumentId, String size) throws NullPointerException;
```
Refer to http api description for parameters and return parameters
## Obtain all market data
```java
    public BaseModel getTickers(String count);
```
Refer to http api description for parameters and return parameters
## Obtain the latest transaction history of a trading pair
```java
public BaseModel getMatches(String product, String start, String end, String page, String perPage) throws NullPointerException;
```
Refer to http api description for parameters and return parameters
## Unfilled order
```java
    public BaseModel getOrderListOpen(RequestOrderListOpenParams params) throws NullPointerException;
```
Refer to http api description for parameters and return parameters
## \Past order
```java
    public BaseModel getOrderListClosed(RequestOrderListClosedParams params) throws NullPointerException;
```
Refer to http api description for parameters and return parameters
## Obtain transaction breakdown
```java
    public BaseModel getDeals(RequestDealsParams params) throws NullPointerException;
```
Refer to http api description for parameters and return parameters
## Obtain transaction records
```java
    public BaseModel getTransactions(RequestTransactionsParams params) throws NullPointerException;
```
Refer to http api description for parameters and return parameters
