# filecoin-api-client

An API client for Filecoin implemented in Java

# Quick Start

> At present, this artifact has not been published to Maven central repository, so you should install locally

```bash
mvn clean install
```

Then import the artifact at pom.xml

```xml
<dependency>
    <groupId>org.rockyang</groupId>
    <artifactId>filecoin-api-client</artifactId>
    <version>0.0.1</version>
</dependency>
```

```java 
Filecoin filecoin = new Filecoin("http://127.0.0.1:3453", false);
// create a new addresss
String address = filecoin.newAddress();

// fetch all address of current node
List<String> addresses = filecoin.getAddressList();

// export an address
String address = "t1b3keswmeuk4tipp5egjbk3aoag56g5zd3cle2va";
KeyInfo keyInfo = filecoin.walletExport(address);

// import wallet
String privateKey = "pdHwTOrJXnAGvQ0861k66xRsiT7N3Ms8IGte3nT837E=";
String address = filecoin.walletImport(privateKey);

// get balance 
String address = "t1esjjrygs7adcfbjnodbpdjzulzobznnln4tmsxq";
BigDecimal balance = filecoin.getBalance(address);
logger.info(balance);

// send transaction  
String from = "t16cgjiwgypve4uup27uk4xgppgd3i4nsldpid6ii";
String to = "t1esjjrygs7adcfbjnodbpdjzulzobznnln4tmsxq";
BigDecimal value = BigDecimal.valueOf(123.456);
BigDecimal gasPrice = BigDecimal.valueOf(0.001);
Integer gasLimit = 300;
String cid = filecoin.sendTransaction(from, to, value, gasPrice, gasLimit);

// get transction status
String cid = "zDPWYqFCtwpgqBEth4wFK53D8Sm9UGxhrL1tueb4RrgFDQLoKC1P";
MessageStatusRes.Message message = filecoin.getTransactionByTxHash(cid);
```

# document | API

The document is building, if you need it urgently, we provide [unit testing](https://github.com/yangjian102621/java-filecoin-api-client/tree/master/src/test/java/org/rockyang/filecoin/test) for each API.

# Contribute

Feel free to dive in! [Open an issue](https://github.com/yangjian102621/java-filecoin-api-client/issues) or submit PRs.





