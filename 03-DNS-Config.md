## DNS and Wildcard DNS configuration

```
-> login over browser
-> Setting > DNS
-> Upstream DNS > google > check for only IPV4
-> DNS domain setting cloud-lab.j2ctechnologies.intern
-> Save
```


## Wildcard DNS setup

```
-> Base dns : cloud-lab.j2ctechnologies.intern
-> prod cluster DNS : prod.cloud-lab.j2ctechnologies.intern |  *.apps.prod.cloud-lab.j2ctechnologies.intern (192.168.0.100)
-> dev cluster DNS : dev.cloud-lab.j2ctechnologies.intern |  *.apps.dev.cloud-lab.j2ctechnologies.intern  (192.168.0.101)
```

```
-> Setting > all setting > Miscellaneous > misc.dnsmasq_lines

address=/apps.prod.cloud-lab.j2ctechnologies.intern/192.168.0.100
address=/apps.prod.cloud-lab.j2ctechnologies.intern/

address=/apps.dev.cloud-lab.j2ctechnologies.intern/192.168.0.101
address=/apps.dev.cloud-lab.j2ctechnologies.intern/


or

address=/apps.prod.cloud-lab.j2ctechnologies.intern/192.168.0.100
server=/apps.prod.cloud-lab.j2ctechnologies.intern/

address=/apps.dev.cloud-lab.j2ctechnologies.intern/192.168.0.101
server=/apps.dev.cloud-lab.j2ctechnologies.intern/

```

```
$ nslookup test.apps.prod.cloud-lab.j2ctechnologies.intern  (192.168.0.100)
$ nslookup test.apps.dev.cloud-lab.j2ctechnologies.intern  (192.168.0.101)
$ nslookup master-1.prod.cloud-lab.j2ctechnologies.intern  (192.168.0.150) add localdns record 
$ nslookup master-1.dev.cloud-lab.j2ctechnologies.intern  (192.168.0.160)  add localdns record
```
