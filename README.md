<h1 align="center">Engram</h1>

<h1 align="center">Kurulum</h1>

```console
# güncelleme
sudo apt update -y && sudo apt upgrade -y

# repoyu klonlayıp yapılandıralım
git clone --recursive https://github.com/engram-network/tokio-docker.git 
cd tokio-docker
chmod +x ./scripts/*.sh

# bash ile scripti çalıştırınca bir kaç yerde y/n soracak y diyebilirsiniz.
bash ./scripts/init-dependency.sh
mkdir -p execution consensus validator
```
```console
# içersine girelim:
sudo nano docker-compose.yml

# aşağıdaki kısımları dosyamızın içinde bulup değiştirelim.
identity=Ruesandora1508
enr-address=IpAdresimiz
graffiti= RuesCommunity
# bu 3 kısmı değiştirin kendinize göre daha sonra CTRL X Y ENTER ile kaydedip çıkalım.
```

<h1 align="center">Log kontrolleri</h1>

```console
# İlk olarak buradan loglara bakıyoruz:
docker logs lighthouse_cl -f
# başta herhangi bir şekilde sync olmayacağını göreceksiniz fakat biraz zaman verin.
```

> sync olmaya çalışıyor: 

![image](https://github.com/ruesandora/Engram/assets/101149671/951a89d4-7c34-4857-a8bd-05e3acba8dd1)

> sync olmaya başladı:

![image](https://github.com/ruesandora/Engram/assets/101149671/8eaaaf47-874a-454b-a1d0-fd27cb4c9077)

```console
# sync işlemleri başladıktan bir kaç dakika sonra
docker logs lighthouse_cl -f
# bu komutu kullanıyoruz ve görseli bıraktım:
```

> sync olmuş versionu aşağıdaki gibidir - güncel blok [burada](https://beaconscan.engram.tech/)

![image](https://github.com/ruesandora/Engram/assets/101149671/838894ba-fffa-46b7-aad4-0ad2c6dc87ed)

<h1 align="center">Deposit işlemleri</h1>



