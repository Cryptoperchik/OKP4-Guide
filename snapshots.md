# Snapshots for OKP4 okp4-nemeton-1 Testnet

## Snapshots are updated every 4 hours

### Snapshots URL: https://okp4-snapshots.stakeangle.com/okp4/

```bash
# Stop service and backup your priv_validator_state.json
sudo systemctl stop okp4d
cp $HOME/.okp4d/data/priv_validator_state.json $HOME/priv_validator_state.json

# Remove old data
okp4d tendermint unsafe-reset-all --home $HOME/.okp4d --keep-addr-book

# Get new data
wget https://okp4-snapshots.stakeangle.com/okp4/data_okp4-nemeton-1.tar
tar -xf data_okp4-nemeton-1.tar -C $HOME/.okp4d/data/

# Get wasm folder
wget https://okp4-snapshots.stakeangle.com/okp4/wasm_okp4-nemeton-1.tar
tar -xf wasm_okp4-nemeton-1.tar -C $HOME/.okp4d/wasm/

# Restore your priv_validator_state.json
mv $HOME/priv_validator_state.json $HOME/.okp4d/data/priv_validator_state.json

# Restart service and check logs
sudo systemctl restart okp4d
sudo journalctl -u okp4d -f -o cat
```
