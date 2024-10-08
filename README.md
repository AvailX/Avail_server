# kalypso-server

##### .env file :

```
# Utils
RPC=https://arb-sepolia.g.alchemy.com/v2/****
PRIVATE_KEY=***********fcedffecda5c639568a869e90
PORT=3030
API_KEY=$2a$12$pDBhELXDyqW3CQj9PUvTTuITUjNAn61Y7UNlrWfcmrbJZfwko7Dxu
SERVER_MODE=DEV  #There are two options, DEV and PROD, using PROD enables API key authentication.
PROOF_REWARD=14500000000000000000
MARKET_ID=19 #Market used for avail proof generation

# Redis configuration
REDIS_HOST=127.0.0.1         # localhost
REDIS_PORT=6379              # default port
REDIS_PASSWORD=password

# Rate Limiting and Throttling
RATE_LIMIT_WINDOW=3600            # 1 hour in seconds
MAX_REQUESTS=10                   # Max requests per window
THROTTLE_DELAY=10                 # 10 seconds delay between requests
```

`Note : If (PROD) SERVER_MODE is provided, please provide a (api-key) in the request headers.`

#### Start the server

```
npm start
```

#### Creating ask and getting execution

#### For public authorization

##### Method: POST

```
http://localhost:3030/proveTx
```

##### Body (raw)

```
{
    "public": "1u16", // network of choice
    "secret": {
        "auth": {
            "requests": [
                {
                    "signer": "aleo1nuh30tkffqcvme0633uphzv2hxv06sr36qs6qgf9zm4asktfyy9qgmxwwm",
                    "network": "1u16",
                    "program": "credits.aleo",
                    "function": "transfer_public",
                    "input_ids": [
                        {
                            "type": "public",
                            "id": "4878891743590214546640132451418316921837303126429229664102982648684530370536field"
                        },
                        {
                            "type": "public",
                            "id": "385601110756643363970932791170630978444219657329262633791049330677150456911field"
                        }
                    ],
                    "inputs": [
                        "aleo1nuh30tkffqcvme0633uphzv2hxv06sr36qs6qgf9zm4asktfyy9qgmxwwm",
                        "100000u64"
                    ],
                    "signature": "sign1nx64532kqlx0dnvn3hdtnj3hu39a4nn7gd9qz2ertaw6574x6up6nv5f7dzmxufg6gam4xrnm4anysl7ulpclwvms8yu5fdvgu5agq564gyzwuc3q0wpn9fqx6zxdr5ztsa693khtz24uzp0vtgazyx4pa5t0dhctgx0u6mh4tx4rkd88ylmmpz76kq0w6hvr57y5gua55nq7vtekqn",
                    "sk_tag": "6879607582454541113355099157081992473302302532410024958090918311816161735890field",
                    "tvk": "6157136090554385763944917283039924505697115464444162148641513003995139100615field",
                    "tcm": "4351447788903622550226496286604204452548226543854984719580287289178605226296field",
                    "scm": "1804530360194380040109520772819533695147338348161909014991940022788006709394field"
                }
            ],
            "transitions": [
                {
                    "id": "au1u0ecvppnlgrhrt8ng00s2zn72mpnqzzfdg57ew6cqwgpkwur8yzsq7aec0",
                    "program": "credits.aleo",
                    "function": "transfer_public",
                    "inputs": [
                        {
                            "type": "public",
                            "id": "4878891743590214546640132451418316921837303126429229664102982648684530370536field",
                            "value": "aleo1nuh30tkffqcvme0633uphzv2hxv06sr36qs6qgf9zm4asktfyy9qgmxwwm"
                        },
                        {
                            "type": "public",
                            "id": "385601110756643363970932791170630978444219657329262633791049330677150456911field",
                            "value": "100000u64"
                        }
                    ],
                    "outputs": [
                        {
                            "type": "future",
                            "id": "6404864214028847942012506566067653215933973663012447120470889954197826941950field",
                            "value": "{\n  program_id: credits.aleo,\n  function_name: transfer_public,\n  arguments: [\n    aleo1nuh30tkffqcvme0633uphzv2hxv06sr36qs6qgf9zm4asktfyy9qgmxwwm,\n    aleo1nuh30tkffqcvme0633uphzv2hxv06sr36qs6qgf9zm4asktfyy9qgmxwwm,\n    100000u64\n  ]\n}"
                        }
                    ],
                    "tpk": "7593140589769740828557392780690886309342370279763445339094104310466050912419group",
                    "tcm": "4351447788903622550226496286604204452548226543854984719580287289178605226296field",
                    "scm": "1804530360194380040109520772819533695147338348161909014991940022788006709394field"
                }
            ]
        },
        "fee_auth": {
            "requests": [
                {
                    "signer": "aleo1nuh30tkffqcvme0633uphzv2hxv06sr36qs6qgf9zm4asktfyy9qgmxwwm",
                    "network": "1u16",
                    "program": "credits.aleo",
                    "function": "fee_public",
                    "input_ids": [
                        {
                            "type": "public",
                            "id": "2363698650055630359966812052567056230728475801846943515400785624457295876722field"
                        },
                        {
                            "type": "public",
                            "id": "3958882729292467774309712296186040551243067823627893095845642931355094945091field"
                        },
                        {
                            "type": "public",
                            "id": "4894933524555310153328484132865679633335161842173769971150129995563470092822field"
                        }
                    ],
                    "inputs": [
                        "297000u64",
                        "297000u64",
                        "127287298127101328958820546105779762806810290041746964330950157926712686859field"
                    ],
                    "signature": "sign14ak3820g0fww6gn4ngjrttc7pqmu5cs767f0j6xp7hr0g6aukvqwyehp64f3rv0v5qjmt5gf5czga7eqp85ver6syzl9zfn87ysa2qv64gyzwuc3q0wpn9fqx6zxdr5ztsa693khtz24uzp0vtgazyx4pa5t0dhctgx0u6mh4tx4rkd88ylmmpz76kq0w6hvr57y5gua55nq7z2e5k7",
                    "sk_tag": "6879607582454541113355099157081992473302302532410024958090918311816161735890field",
                    "tvk": "7901151033091423262623598339242963680419288031662259716248723637702582125208field",
                    "tcm": "7051601920388875605940149236219173211698128795350212809828128423518804631884field",
                    "scm": "1627896614972599948208497570809140636926824745550202787992237913205830631250field"
                }
            ],
            "transitions": [
                {
                    "id": "au1dh6z6xvshrl9ptwk7eec4e3p8uyef9hj9w6pckt7mkvwezscrv9suyndmu",
                    "program": "credits.aleo",
                    "function": "fee_public",
                    "inputs": [
                        {
                            "type": "public",
                            "id": "2363698650055630359966812052567056230728475801846943515400785624457295876722field",
                            "value": "297000u64"
                        },
                        {
                            "type": "public",
                            "id": "3958882729292467774309712296186040551243067823627893095845642931355094945091field",
                            "value": "297000u64"
                        },
                        {
                            "type": "public",
                            "id": "4894933524555310153328484132865679633335161842173769971150129995563470092822field",
                            "value": "127287298127101328958820546105779762806810290041746964330950157926712686859field"
                        }
                    ],
                    "outputs": [
                        {
                            "type": "future",
                            "id": "4691267870809680196082081639632552709802937621836484012634785392877413036681field",
                            "value": "{\n  program_id: credits.aleo,\n  function_name: fee_public,\n  arguments: [\n    aleo1nuh30tkffqcvme0633uphzv2hxv06sr36qs6qgf9zm4asktfyy9qgmxwwm,\n    594000u64\n  ]\n}"
                        }
                    ],
                    "tpk": "834676624733568110369271641036842053056234169779041948644838943710920111412group",
                    "tcm": "7051601920388875605940149236219173211698128795350212809828128423518804631884field",
                    "scm": "1627896614972599948208497570809140636926824745550202787992237913205830631250field"
                }
            ]
        }
    }
}
```
