# chia.template

```bash
chia init
chia keys generate
chia configure -t true
curl -LO https://download.chia.net/testnet10/blockchain_v2_testnet10.sqlite.gz
gunzip -c blockchain_v2_testnet10.sqlite.gz > $CHIA_ROOT/db/blockchain_v2_testnet10.sqlite
```
```bash
chia keys show --show-mnemonic-seed
```