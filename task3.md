<p style="font-size:14px" align="right">
<a href="https://t.me/PemulungAirdropID" target="_blank">Join our telegram <img src="https://user-images.githubusercontent.com/72949170/194228482-0f875615-e155-4b12-8716-8111addd6cba.jpg" width="30"/></a>
</p>

<p align="center">
  <img height="50" height="auto" src="https://user-images.githubusercontent.com/38981255/184088981-3f7376ae-7039-4915-98f5-16c3637ccea3.PNG">
</p>

# INERY Task 3

## 1. Update dan install package

```
sudo apt update -y && sudo apt upgrade -y
sudo apt install -y make bzip2 automake libbz2-dev libssl-dev doxygen graphviz libgmp3-dev \
autotools-dev libicu-dev python2.7 python2.7-dev python3 python3-dev \
autoconf libtool curl zlib1g-dev sudo ruby libusb-1.0-0-dev \
libcurl4-gnutls-dev pkg-config patch llvm-7-dev clang-7 vim-common jq libncurses5 git
```

```
git clone https://github.com/inery-blockchain/inery.cdt
```

```
export PATH=$PATH:$HOME/inery.cdt/bin/ >> $HOME/.bash_profile
source $HOME/.bash_profile
```

## 2. Write Code

Langsung paste aja 


```
sudo tee $HOME/inrcrud/inrcrud.cpp >/dev/null <<EOF
#include <inery/inery.hpp>
#include <inery/print.hpp>
#include <string>

using namespace inery;

using std::string;

class [[inery::contract]] inrcrud : public inery::contract {
  public:
    using inery::contract::contract;


        [[inery::action]] void create( uint64_t id, name user, string data ) {
            records recordstable( _self, id );
            auto existing = recordstable.find( id );
            check( existing == recordstable.end(), "record with that ID already exists" );
            check( data.size() <= 256, "data has more than 256 bytes" );

            recordstable.emplace( _self, [&]( auto& s ) {
               s.id         = id;
               s.owner      = user;
               s.data       = data;
            });

            print( "Hello, ", name{user} );
            print( "Created with data: ", data );
        }

         [[inery::action]] void read( uint64_t id ) {
            records recordstable( _self, id );
            auto existing = recordstable.find( id );
            check( existing != recordstable.end(), "record with that ID does not exist" );
            const auto& st = *existing;
            print("Data: ", st.data);
        }

        [[inery::action]] void update( uint64_t id, string data ) {
            records recordstable( _self, id );
            auto st = recordstable.find( id );
            check( st != recordstable.end(), "record with that ID does not exist" );


            recordstable.modify( st, get_self(), [&]( auto& s ) {
               s.data = data;
            });

            print("Data: ", data);
        }

            [[inery::action]] void destroy( uint64_t id ) {
            records recordstable( _self, id );
            auto existing = recordstable.find( id );
            check( existing != recordstable.end(), "record with that ID does not exist" );
            const auto& st = *existing;

            recordstable.erase( st );

            print("Record Destroyed: ", id);

        }

  private:
    struct [[inery::table]] record {
       uint64_t        id;
       name     owner;
       string          data;
       uint64_t primary_key()const { return id; }
    };

    typedef inery::multi_index<"records"_n, record> records;
 };
EOF
```

![image](https://user-images.githubusercontent.com/72949170/199278083-e9545367-eae9-4afa-8fda-a71b55f8b627.png)


## 3. Compile Code

```
inery-cpp $HOME/inrcrud/inrcrud.cpp -o $HOME/inrcrud/inrcrud.wasm
```

![image](https://user-images.githubusercontent.com/72949170/199278974-28fcdf5b-58e3-4dee-965f-6394f6fd5869.png)


## 4. Open dan Unlock Wallet

```
cline wallet unlock -n Your-account
```

Ganti ```Your-account``` jadi nama akun kalian

- Masukan passwod wallet kalian dari ```file.txt``` yang dulu

![image](https://user-images.githubusercontent.com/72949170/199279205-ce7b8d8e-3fd2-4149-b76e-ee7813ea5c4a.png)


## 5. Set contract

```
cline set contract Your-account ./inrcrud
```

![image](https://user-images.githubusercontent.com/72949170/199279394-70b2943e-61c7-4140-8c5e-7d6e2250b84a.png)

- Create

```
cline push action Your-account create '[1, "Your-name-account", "My first Record"]' -p Your-account --json
```

![image](https://user-images.githubusercontent.com/72949170/199279801-81c4cd58-4d4f-4363-9443-7151f0c3ed9e.png)

- Read

```
cline push action Your-account read [1] -p Your-account --json
```

![image](https://user-images.githubusercontent.com/72949170/199280326-e56bde04-4d49-4c5f-8c78-e59337410302.png)

- Update

```
cline push action Your-account update '[ 1,  "My first Record Modified"]' -p Your-account --json
```

![image](https://user-images.githubusercontent.com/72949170/199280666-a8195a76-9b67-4c99-a9df-d659392d8c76.png)

- Destroy

```
cline push action Your-account destroy [1] -p Your-account --json
```

![image](https://user-images.githubusercontent.com/72949170/199280830-0818ee54-8614-4042-b003-b5da5868f03c.png)

- DONE

**Jangan lupa klik ```Finish Task``` di dashboard inery**

