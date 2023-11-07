<h1 align="center">Engram Network</h1>

> Kurulum nedenlerim: Donanım düşük, teşvikle, kısa sürecek ve sınırlı katılımcı.

> Tüm süreç [burada](https://engramnet.io/engram-tokio-testnet-program/) listeli.

> Önemli linkler: [Duyuru](https://t.me/RuesAnnouncement) - [Sohbet](https://t.me/RuesChat) -  [WP Kanalı](https://whatsapp.com/channel/0029VaBcj7V1dAw1H2KhMk34) - [Discord](https://discord.gg/pmaaU4J2)

<h1 align="center">Donanımm</h1>

> [Hetzner](https://github.com/ruesandora/Hetzner) kullanıyorum.

```
2 CPU - 4 RAM - 40 SSD - Ubuntu
```

<h1 align="center">Kurulum</h1>

```console
# güncelleme
sudo apt update -y && sudo apt upgrade -y

# repoyu klonlayıp yapılandıralım
git clone --recursive https://github.com/engram-network/tokio-docker.git
cd tokio-docker

# gerekli paketler için asdf scriptini çalıştıralım
./scripts/install-asdf.sh

mkdir -p execution consensus validator
```
```console
# içersine girelim:
sudo nano docker-compose.yml

# aşağıdaki kısımları dosyamızın içinde bulup değiştirelim.
identity=Ruesandora
enr-address=IpAdresimiz
graffiti=discordİsmi
# bu 3 kısmı değiştirin kendinize göre daha sonra CTRL X Y ENTER ile kaydedip çıkalım.

# docker'i yükleyelim
./scripts/install-docker.sh

# ve run edelim
docker compose up -d
```

<h1 align="center">Log kontrolleri</h1>

> Loglar sizde farklı olabilir benim kurulumum eskiye ait, güncel versionunu yüklüyorsunuz siz.

```console
# İlk olarak buradan loglara bakıyoruz:
docker logs lighthouse_cl -f
# başta herhangi bir şekilde sync olmayacağını göreceksiniz fakat biraz zaman verin.
```

> sync olmaya çalışıyor: 

![image](https://github.com/ruesandora/Engram/assets/101149671/d042ce55-0131-4ee6-8b39-8d3d81f0b704)

> sync olmaya başladı:

![image](https://github.com/ruesandora/Engram/assets/101149671/e6f205d9-b938-4bb9-aac8-3f18863df468)


```console
# sync işlemleri başladıktan bir kaç dakika sonra
docker logs lighthouse_cl -f
# bu komutu kullanıyoruz ve görseli bıraktım:
```

> sync olmuş versionu aşağıdaki gibidir - güncel blok [burada](https://beaconscan.engram.tech/)

![image](https://github.com/ruesandora/Engram/assets/101149671/5feac68e-2cac-4dba-b15a-dc100f8f9632)


<h1 align="center">Deposit işlemleri</h1>

```console
# bu komut ile mnemonic oluşturuyor ve yedekliyoruz, akabinde bir EVM cüzdana import ediyoruz.
eth2-val-tools mnemonic
```

> Çıkan 24 kelimeyi metamaska import edin.

> Discord faucet request kanalından token isteyin

```console
# içersine giriyoruz
nano ./scripts/validator-deposit-data.sh

# Aşağıdaki kısımları değiştiriyoruz:
amount: # 32000000000
withdrawals-mnemonic: # yukarda oluşturduğumuz mnemonicleri giriyoruz
validators-mnemonic: # yukarda oluşturduğumuz mnemonicleri giriyoruz
from: # mnemonicleri import ettiğimiz ve token aldığımız cüzdan adresi
privatekey: # mnemonicleri import ettiğimiz cüzdanın private keyi

# Deposit ile işlemi bitiriyoruz
bash ./scripts/validator-deposit-data.sh
```

# Kurulum sonrası

> [Bu](https://docs.google.com/forms/d/e/1FAIpQLSeDF_UA5IDI49vJ99EmumHq3eyLhdiVaENTyobw2Egg9AgYhQ/viewform) formu doldurun ve bir kaç gün içinde [burada](https://nodemon.engram.tech/) listeleneceksiniz.









