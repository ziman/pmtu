## pmtu

A quick'n'dirty Path MTU discovery script in Python that automates repeated
calls to `ping` to perform binary search.

Sometimes the network is unusable without manually decreasing the MTU on the
interface. This script should tell you what the appropriate value is.

### Example

```
$ ./pmtu example.com
750: 64.0 % packet loss
1125: 50.0 % packet loss
1312: 73.0 % packet loss
1406: 54.0 % packet loss
1453: * * *
1429: 50.0 % packet loss
1441: 44.0 % packet loss
1447: 0.0 % packet loss
1450: 61.0 % packet loss
1451: 54.0 % packet loss
1452: 37.0 % packet loss
>>> optimal MTU: 1452 + 28 = 1480

$ ip link set mtu 1480 dev wlan0
```

### Disclaimer

It's really quick'n'dirty, just about usable for my personal purposes.

### License

BSD 3-clause.
