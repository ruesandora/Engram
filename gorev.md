<h1 align="center">Engram Network 2. Hafta Görevleri</h1>

Bu Forma Giriyoruz 

> https://docs.google.com/forms/d/e/1FAIpQLSeDF_UA5IDI49vJ99EmumHq3eyLhdiVaENTyobw2Egg9AgYhQ/viewform

<h1 align="center">Açılan Formda Bilgilerimizi girip alttaki sonraki butonuna basıyoruz.</h1>

1- Alttaki Repoyu forklayıp kendi linkimizi giriyoruz.
> https://github.com/engram-network/tokio-docker

2- Engram Test için kullandığımız walleti giriyoruz. (Node içindeki)

3- Engram kurulu olduğu sunucumuza giriyoruz ve ``` curl http://localhost:5052/eth/v1/node/identity | jq ``` komutunu giriyoruz. Çıktıdan "enr:- ....." iki tırnak arasını, uzun kısmını kopyalayıp girelim.

4- ``` docker exec -it striatum_el striatum attach --exec "admin.nodeInfo.enode" http://localhost:8545 ``` kodunu girelim. Çıktıdan "enode:....." iki tırnak arasını, uzun kısmını kopyalayıp girelim.
Birinci hafta görevleri bitti. Şimdi 2. hafta görevleri

<br> 

<h1 align="center">Aynı formda "Sonraki" diyoruz "Week 2 Submission" görevleri geliyor. Thirtweb ile yapamazsanız Remixi kullanın.</h1>

<br>
1. Görev için Token Kontratı Deploy etmemiz gerek, ThirdWeb ile olan yöntem olmazsa, Remix ile olan yöntemi dene. İkisini de yapmana gerek yok

# Thirdweb ile olan Yöntem (ERC-20 DEPLOY GÖREVİ)

1- https://thirdweb.com engram test wallet ile giriş yaptım/ üye oldum. 
faucet-tokio.engram.tech faucetten token alalım.
https://thirdweb.com/dashboard/contracts/deploy +deploy contract, token, deploy now sırası ile tıklayalım. Sağ tarafta en atlta ağı seçelim açılan pencere "add custom network" tıklayıp elle bilgileri girelim. Deplow now dediğimizde işimiz bitiyor.

Engram Test Network RPC:
Blockchain Name: Engram Tokio Testnet
RPC Address: https://engram.tech/testnet
Chain ID: 130
Ticker: tGRAM

## tx başarılı olduysa https://scan.engram.tech/ sitesine girip kontrat tx i bulup cevap olarak giriyoruz.

# Remix ile olan Yöntem (ERC-20 DEPLOY GÖREVİ)

1- Metamaska Engram Testnet Ağını ekleyelim.
```
Network name
Engram Test Network

RPC URL
https://engram.tech/testnet

Chain ID
130

Currency symbol
tGRAM

Block explorer URL
https://scan.engram.tech/
```
2- Alttaki Faucetten token alalım (Engram için olan cüzdana)
> https://faucet-tokio.engram.tech/

2- Remixin sitesine girelim
>https://remix.ethereum.org/#optimize=false&runs=200&evmVersion=null&version=soljson-v0.8.17+commit.8df45f5f.js&lang=en

3- Soldaki contract klasörüne sağ tıklayıp, New File diyoruz isim olarak Token.sol giriyoruz. Sonra tıklayıp içine alttaki kodu yapıştırıyoruz, Belirttiğim yerleri değiştirin!

> string public name = "TOKENADINIZ";

> string public symbol = "TOKENKISALTMASI 4 HANELI KOYUN ÖRNEK RUES";
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ERC20Token {
    string public name = "TOKENADINIZ";
    string public symbol = "TOKENKISALTMASI 4 HANELI KOYUN ÖRNEK RUES";
    uint8 public decimals = 18;
    uint256 public totalSupply = 1000000 * 10**uint256(decimals);

    mapping(address => uint256) public balanceOf;
    mapping(address => mapping(address => uint256)) public allowance;

    event Transfer(address indexed from, address indexed to, uint256 value);
    event Approval(address indexed owner, address indexed spender, uint256 value);

    constructor() {
        balanceOf[msg.sender] = totalSupply;
    }

    function transfer(address to, uint256 value) public returns (bool success) {
        require(to != address(0), "Invalid address");
        require(balanceOf[msg.sender] >= value, "Insufficient balance");

        balanceOf[msg.sender] -= value;
        balanceOf[to] += value;

        emit Transfer(msg.sender, to, value);
        return true;
    }

    function approve(address spender, uint256 value) public returns (bool success) {
        require(spender != address(0), "Invalid address");

        allowance[msg.sender][spender] = value;

        emit Approval(msg.sender, spender, value);
        return true;
    }

    function transferFrom(address from, address to, uint256 value) public returns (bool success) {
        require(from != address(0), "Invalid address");
        require(to != address(0), "Invalid address");
        require(balanceOf[from] >= value, "Insufficient balance");
        require(allowance[from][msg.sender] >= value, "Allowance exceeded");

        balanceOf[from] -= value;
        balanceOf[to] += value;
        allowance[from][msg.sender] -= value;

        emit Transfer(from, to, value);
        return true;
    }
}
```
Sonra alttaki görselde 1. yere tıklıyoruz, 2. yerde Injected Provider - Metamaskı seçiyoruz, 3. Yerde Deploy butonuna basıyoruz! Bu işlemleri Engram Ağında yaptığınıza emin olun!

![image](https://github.com/ruesandora/Engram/assets/76253089/fadbf2ac-37f2-4d31-a16d-921c1046042e)

## Tx başarılı olduysa https://scan.engram.tech/ sitesine girip kontrat tx i bulup cevap olarak giriyoruz.

2. Görevin cevabı ERC20
3. Görev: Tokenimize İsim giriyoruz (Formdaki örnek gibi)
4. Görev: Tokenimizin amacı nedir (Formdaki örneğe göre bir şeyler yazın)

