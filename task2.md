<p style="font-size:14px" align="right">
<a href="https://t.me/PemulungAirdropID" target="_blank">Join our telegram <img src="https://user-images.githubusercontent.com/72949170/194228482-0f875615-e155-4b12-8716-8111addd6cba.jpg" width="30"/></a>
</p>

<p align="center">
  <img height="50" height="auto" src="https://user-images.githubusercontent.com/38981255/184088981-3f7376ae-7039-4915-98f5-16c3637ccea3.PNG">
</p>

# INERY Task 2

Dokumen Official :
> [Create Token](https://docs.inery.io/docs/create-token-3/)

## Sebelum Task 2, Pastikan Task 1 udah kelar
https://github.com/muhamad-ramadhani/inery/blob/main/master-node.md


**Langsung Kita Mulai Aja**

## 1. Unlock Wallet
```
cline wallet unlock -n NamaWallet
```
Masukan password dari file.txt file (YTTA kalau udah garap task 1)

## 2. Generate file token.abi dan token.wasm
```
cline get code inery.token -c token.wasm -a token.abi --wasm
```

## 3. Set Wasm
```
cline set code -j NamaAkun token.wasm
```
> **Output**
>
>Reading WASM from /root/token.wasm... Setting Code... executed transaction: 31b009ed4010adc959e1d5177be0213a4a39e87668fe01f3e8ed076c5827a12d 7536 bytes 2281 us # inery <= inery::setcode {"account":"token22","vmtype":0,"vmversion":0,"code":"0061736d0100000001a0011b60000060017e0060027f7f...

## 4. Set Abi
```
cline set abi NamaAkun token.abi
```
> **Output**
> 
>Setting ABI... executed transaction: 11e840da507ac57c76bdcef13114cb7922037d7d53e53cf8685def8d9e7c4d0d 1280 bytes 390 us # inery <= inery::setabi {"account":"token22","abi":"0e696e6572793a3a6162692f312e310008076163636f756e7400010762616c616e636505...

## 5. Buat Token
```
cline push action NamaAkun create '["NamaAkun", "50000.0000 ASW" , "creating my first tokens"]' -p NamaAkun
```
> **output**
>
>executed transaction: 8492c49f08d37a5522409ccbd73b7c3f61751639cad08d981135936dd61567aa 120 bytes 163 us # token22 <= token22::create {"issuer":"token22","maximum_supply":"50000.0000 ASW"}

## 6. Deploy atau Issue Token
```
cline push action NamaAkun issue '["NamaAkun", "5000.0000 ASW", "Issuing some ASW token"]' -p NamaAkun
```
>**output**
>
>executed transaction: a62c24d015c0d5df43fba6e1b0d4d638f83d2fc49d4e2243e3142956902e9b55 136 bytes 205 us # token22 <= token22::issue {"to":"token22","quantity":"5000.0000 ASW","memo":"Issuing some ASW token"}

## 7. LAST, Transfer Token Ke 10 Address (termasuk address inery)
```
cline push action NamaAkun transfer '["NamaAkun", "TargetAkun", "5,000 ASW", "Here you go 1 ASW for free :) "]' -p NamaWallet
```
>**Output**
>
>executed transaction: 5c820fef47c42a5b056d1b60741000aa90b621e89edf621bbf35c1263b9a460e 136 bytes 223 us # token22 <= token22::transfer {"from":"token22","to":"test22","quantity":"5.0000 ASW","memo":"memo"} # test22 <= token22::transfer {"from":"token22","to":"test22","quantity":"5.0000 ASW","memo":"memo"}

## Cek token kalian kalau udah dikirim ke inery atau address lain
```
cline get currency balance inery.token inery
```

### DONE SIR
## JANGAN LUPA JOIN TELEGRAM
## HTTPS://T.ME/PEMULUNGAIRDROPID
