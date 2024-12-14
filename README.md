```sh
sudo apt-get update
sudo apt-get install build-essential git libnuma-dev 

git clone https://git.kernel.org/pub/scm/utils/rt-tests/rt-tests.git
cd rt-tests
make
sudo make install

sudo cyclictest -t4 -p1 -i100 -l1000000
```

realtime:
```sh
orangepi@orangepizero2w:~$ sudo cyclictest --mlockall --smp --priority=80 --interval=200 --distance=0
[sudo] password for orangepi:
# /dev/cpu_dma_latency set to 0us
policy: fifo: loadavg: 1.04 1.00 0.54 1/150 2022

T: 0 ( 2013) P:80 I:200 C:1546988 Min:      6 Act:   18 Avg:   16 Max:     306
T: 1 ( 2014) P:80 I:200 C:1546942 Min:      6 Act:   13 Avg:   16 Max:     342
T: 2 ( 2015) P:80 I:200 C:1546914 Min:      6 Act:   13 Avg:   16 Max:     399
T: 3 ( 2016) P:80 I:200 C:1546880 Min:      5 Act:   18 Avg:   16 Max:     333

```

default:
```sh
orangepi@orangepizero2w:~$ uname -r
6.1.31-sun50iw9
orangepi@orangepizero2w:~$ sudo cyclictest --mlockall --smp --priority=80 --interval=200 --distance=0
# /dev/cpu_dma_latency set to 0us
policy: fifo: loadavg: 1.27 1.19 0.94 2/161 4702

T: 0 ( 4234) P:80 I:200 C:1001283 Min:      4 Act:   12 Avg:   13 Max:    8380
T: 1 ( 4235) P:80 I:200 C:1001047 Min:      4 Act:   15 Avg:   13 Max:    8408
T: 2 ( 4236) P:80 I:200 C:1005574 Min:      4 Act:   29 Avg:   12 Max:    6719
T: 3 ( 4237) P:80 I:200 C:1005628 Min:      4 Act:   19 Avg:   13 Max:    9070
```
