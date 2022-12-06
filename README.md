# ipset-email-blacklist
메일서버에 접근하는 수많은 IP중에서 계속 불법인증을 시도하는 해외IP 대역만 뽑아서 ipset를 구성해 보았습니다.
이 IP들을 iptables를 이용하여 smtp와 pop3 접근을 막았더니 효과가 아주 좋습니다.

```sh
iptables -I INPUT -p tcp --match multiport --dport 25,110 -m set --match-set blockip src -j DROP
```

주기적으로 계속 업데이트할 예정입니다.
