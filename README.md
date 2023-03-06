# nolus-rila-snapshot


Stop node
```
sudo systemctl stop nolusd
```
Save priv_validator_state and delete data folder

```
cp $HOME/.nolus/data/priv_validator_state.json $HOME/.nolus/priv_validator_state.json.backup
rm -rf $HOME/.nolus/data
```
Make data dir and download snapshot
```
mkdir $HOME/.nolus/data
wget -O - http://5.161.60.42:82/nolus/nolus-rila_latest.tar | tar xf - -C $HOME/.nolus/data
```
Move your priv_validator_state back
```
mv $HOME/.nolus/priv_validator_state.json.backup $HOME/.nolus/data/priv_validator_state.json

```
Restart node and check log
```
sudo systemctl start nolusd && sudo journalctl -u nolusd -f --no-hostname -o cat
```


