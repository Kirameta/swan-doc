# Configuration

Before creating a task, you should update your configuration in `~/.swan/client/config.toml` to ensure it is right.

```
vi ~/.swan/client/config.toml
```

```
    [lotus]
    client_api_url = "http://[ip]:[port]/rpc/v0"   # Url of lotus client web API, generally the [port] is 1234
    client_access_token = ""                       # Access token of lotus client web API, it should have admin access right

    [main]
    market_version = "1.1"                         # Send deal type, 1.1 or 1.2, config(market_version=1.1) is DEPRECATION, will REMOVE SOON (default: "1.1")
    api_url = "https://go-swan-server.filswan.com" # Swan API address. For Swan production, it is `https://go-swan-server.filswan.com`. It can be ignored if `[sender].offline_swan=true`
    api_key = ""                                   # Swan API key. Acquired from [Swan Platform](https://console.filswan.com/#/dashboard) -> "My Profile"->"Developer Settings". It can be ignored if `[sender].offline_swan=true`.
    access_token = ""                              # Swan API access token. Acquired from [Swan Platform](https://console.filswan.com/#/dashboard) -> "My Profile"->"Developer Settings". It can be ignored if `[sender].offline_swan=true`.

    [ipfs_server]
    download_url_prefix = "http://[ip]:[port]"     # IPFS server URL prefix. Store CAR files for downloading by the storage provider. The downloading URL will be `[download_url_prefix]/ipfs/[dataCID]`
    upload_url_prefix = "http://[ip]:[port]"       # IPFS server URL for uploading files

    [sender]
    offline_swan = false                           # Whether to create a task on [Swan Platform](https://console.filswan.com/#/dashboard), when set to true, only generate metadata for Storage Providers to import deals. 
    verified_deal = true                           # Whether deals in the task are going to be sent as verified or not
    fast_retrieval = true                          # Whether deals in the task are available for fast-retrieval or not
    skip_confirmation = false                      # Whether to skip manual confirmation of each deal before sending
    generate_md5 = false                           # Whether to generate md5 for each CAR file and source file(resource consuming)
    wallet = ""                                    # Wallet used for sending offline deals
    max_price = "0"                                # Max price willing to pay per GiB/epoch for offline deals
    start_epoch_hours = 96                         # Specify hours that the deal should start after at (default 96 hours)
    expire_days = 4                                # Specify days that the deal will expire after (default 4 days) 
    duration = 1512000                             # How long the Storage Providers should store the data for, in blocks(the 30s/block), default 1512000.
    start_deal_time_interval = 500                 # The interval between two deals sent, default: 500ms
```
