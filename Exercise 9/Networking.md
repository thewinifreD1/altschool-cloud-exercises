Given the following IP address/CIDR: **193.16.20.35/29**

- what is the Network IP
- number of hosts
- range of IP addresses
- broadcast IP from this subnet


#### Procedure:

To solve this you have to first figure out the subnet mask from the given CIDR (/29)

Converting it to binary then gives:

**Network Portion:** 1's

**Host Portion:** 0's

**Netmask Binary:** 11111111.11111111.11111111.11111000

Then inorder to convert the subnet mask address from binary to decimal apply the following formular

> Note: In the binary system there are only 1s and 0s. They get different values depending on their positions in the octet. Each position is a power of 2. To get the decimal number you have to sum up those numbers.

| First Octet  | Second Octet | Third Octet | Fourth Octet | Fifth Octet | Sixth Octet | Seventh Octet | Eight Octet |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
|  2^<sup>7</sup> | 2^<sup>6</sup>  | 2^<sup>5</sup>  | 2^<sup>4</sup>  | 2^<sup>3</sup> | 2^<sup>2</sup>  | 2^<sup>1</sup>  | 2^<sup>0</sup>  |
| 128  | 64  | 32  | 16  | 8  | 4  | 2  | 1  |

Total no. of octets in binary: 128 + 64 + 32 + 16 + 8 + 4 + 2 + 1

                             = 255

The **first & last IP adress** will be reserved for the network and broadcast so:


Given IP: **193.16.20.35/29**

Network IP: **193.16.20.32**

Number of Hosts: **6**

Range of IP Addresses: **193.16.20.33** - **193.16.20.38**
 
- min range of IP's = **193.16.20.33**
 - max range of IP's = **193.16.20.38**

Broadcast IP: **193.16.20.39**
