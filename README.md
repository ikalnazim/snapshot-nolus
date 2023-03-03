# Snapshot-nolus

How to Install Snapshot Nolus by Nematodes

# Stop service nolus first and reset data (copy it one by one) 
    sudo systemctl stop nolusd
    
    cp $HOME/.nolus/data/priv_validator_state.json $HOME/.nolus/priv_validator_state.json.backup
    
    rm -rf $HOME/.nolus/data
    
# Download Snapshot Nolus by Nematodes
    wget -O nolus-snapshot-20230303.tar.lz4 https://snapshot.nolus-testnet.nematodes.tech/nolus/nolus-snapshot-20230303.tar.lz4 --inet4-only
  then

    `lz4 -c -d nolus-snapshot-20230303.tar.lz4 | tar -x -C $HOME/.nolus`
  
# Restart service Nolus
    sudo systemctl start nolusd
  
# Check the logs
    sudo journalctl -u nolusd -f --no-hostname -o cat
    
# Done
