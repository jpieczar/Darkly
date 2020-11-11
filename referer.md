**http://10.0.0.12/?page=e43ad1fdc54babe674da7c7b8f0127bde61de3fbe01def7d00f151c2fcca6d1c**

This page is entirely in French but has some interesting comments once is is inspected.
The comments provide information on how to get the flag by coming from the following site:
https://www.nsa.gov/
It also mentions that this must be its user agent:
Let's use this browser : "ft\_bornToSec".

Using cURL, it is possible to get the flag.
_curl -H "User-Agent: ft_bornToSec" --referer https://www.nsa.gov/ http://10.0.0.12/?page=e43ad1fdc54babe674da7c7b8f0127bde61de3fbe01def7d00f151c2fcca6d1c | grep "flag"_
Grep is used to easily find the flag.

**FLAG
f2a29020ef3132e01dd61df97fd33ec8d7fcd1388cc9601e7db691d17d4d6188**
