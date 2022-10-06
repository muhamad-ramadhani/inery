<p style="font-size:14px" align="right">
<a href="https://t.me/PemulungAirdropID" target="_blank">Join our telegram <img src="https://user-images.githubusercontent.com/50621007/183283867-56b4d69f-bc6e-4939-b00a-72aa019d1aea.png" width="30"/></a>
</p>

<p align="center">
  <img height="50" height="auto" src="https://user-images.githubusercontent.com/38981255/184088981-3f7376ae-7039-4915-98f5-16c3637ccea3.PNG">
</p>

# Tutorial Become a Master Node

Dokumen Official :
> [Node Lite & Master](https://docs.inery.io/docs/category/lite--master-nodes)

Explorer :
> [Explorer Inary](https://explorer.inery.io/ "Explorer Inary")

## Sebelum Menjalankan Node Register Akun Testnet Dulu
**Daftar dulu disini :** https://github.com/muhamad-ramadhani/inery-node/blob/main/register.md

## 1. Update Tools Yang di Perlukan

<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/38981255/184288420-51676f99-2069-417c-aa9e-cdf28a24e9dd.PNG">
</p>

```
sudo apt-get update && sudo apt install git && sudo apt install screen
```

<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/38981255/184288416-3eab98fb-2544-4be8-bae2-f6c99210750d.PNG">
</p>

```
sudo apt-get install -y make bzip2 automake libbz2-dev libssl-dev doxygen graphviz libgmp3-dev \
autotools-dev libicu-dev python2.7 python2.7-dev python3 python3-dev \
autoconf libtool curl zlib1g-dev sudo ruby libusb-1.0-0-dev \
libcurl4-gnutls-dev pkg-config patch llvm-7-dev clang-7 vim-common jq libncurses5
```
## 2. On Port (optional)
```
ufw allow 22 && ufw allow 8888 && ufw allow 9010 && ufw enable -y
```
## 3. Mulai Node

<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/38981255/184288675-1c551b8f-f882-45d9-9058-ae95c7888963.PNG">
</p>

```
git clone https://github.com/inery-blockchain/inery-node
```
## 4. Explorer BIN
```
cd inery-node
```
## 5. Beri Izin File

<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/38981255/184288914-bcea524f-d32e-4460-a971-913af8c359a9.PNG">
</p>

```
cd inery.setup
```
```
chmod +x ine.py
```
```
./ine.py --export
```
```
cd; source .bashrc; cd -
```
## 6. Become a Master Node

## 7. Buka Config Kalian Lalu Edit, Perintahnya : 
```
cd inery-node/inery.setup
```
```
cd tools
```
```
nano config.json
```
untuk mengonfigurasi node dengan informasi Akun Anda, Tolong Perhatikan dan Teliti

<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/72949170/194227034-1c1dbdb8-2c3e-4296-832f-038dc9705650.jpg">
</p>

**Penting:** Untuk Pengguna VPS Azure IP bisa di isi Dengan IP Private Kalian Cari Jalankan Perintah `hostname - i`

Pastikan Data Sama Dengan [Akun Testnet](https://github.com/muhamad-ramadhani/inery-node/blob/main/register.md "Akun Testnet") Yang ada di Dasboard Akun Yang Sudah Kalian Buat

Simpan (ctrl+x), Ketik "Y" dan keluar (enter)

## 8. Mulai Protocol Blockchain
<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/38981255/184290968-0dd5773f-6c08-4a5d-a5a2-11c4db67678b.PNG">
</p>

```
cd inery-node/inery.setup
```
```
screen -R master
```
```
./ine.py --master
```
<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/72949170/194225311-fee437f0-db09-4669-a9e5-1f826586cacf.jpg">
</p>
Jika Sudah Seperti Gambar di Atas, Artinya Sudah jalan dan Tunggu Sampai 1 - 2 Jam Untuk Mensinkronkan 
**Ketik CTRL + A + D** Untuk jalan di Background dan Untuk Kembali lagi Ke Screen Gunakan Perintah `screen -Rd master`

<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/72949170/194225739-3da9e698-b097-4411-80d0-45c58c1fca5c.jpg">
</p>

Jika Sudah Seperti gambar di atas, Artilnya Sudah Selesai Sinkron, Silahkan Lanjut Next Step

## 12. Start Node
### Lakukan Ini di TAB Baru
```
cd ~/inery-node/inery.setup/master.node/
./start.sh
```
## 13. Daftar dan setujui (Menghubungkan Wallet dengan Dasboard Akun)

### Lakukan Ini Masih di TAB Baru

<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/72949170/194226248-c72f921f-e7ff-4a10-b8fe-d7f13597a8ce.jpg">
</p>

```
cline wallet create -n <your_name_wallet> -f file.txt
```
file.txt berisi Password Wallet kalian (Kalian membutuhkan itu Jika Wallet kalian dalam Keadaan Lock)
```
cline wallet import --private-key <your_private_key> -n <your_name_wallet>
```
Import Private Key kalian ke Wallet

### Daftar sebagai produser dengan menjalankan perintah:

```
cline system regproducer <your_account> <your_public_key> 0.0.0.0:9010
```
```
cline system makeprod approve <your_account> <your_account>
```
Semua Perintah di atas Jalankan tanpad tanda (<>)

Lalu balik ke website nya, klik "FINISH TASK"
<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/72949170/194227741-eb209ffa-ea77-4084-b182-307e8c1333dd.jpg">
</p>


<p align="center">
  <img height="auto" height="auto" src="https://user-images.githubusercontent.com/72949170/194226619-7820241f-3a7e-4b07-8c82-f7fc62b71d17.jpg">
</p>

**Note :** Silahkan Check di Explorer Inery ,Tutorial Master Node Selesai!

# Perintah Berguna 

## Check Saldo Wallet 
```
cline get currency balance inery.token ACCOUNT_NAME
```
## Delete Wallet di Node
```
cline wallet stop
```
```
rm -rf inery-wallet
rm -rf file.txt
rm -rf defaultWallet.txt
```
