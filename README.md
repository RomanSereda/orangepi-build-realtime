```sh
sudo apt-get update
sudo apt-get install build-essential git libnuma-dev 

git clone https://git.kernel.org/pub/scm/utils/rt-tests/rt-tests.git
cd rt-tests
make
sudo make install

sudo sh -c "echo -1 > /proc/sys/kernel/sched_rt_runtime_us"

ssh_1: sudo cyclictest --mlockall --smp --priority=80 --interval=200 --distance=0
ssh_2: sudo apt update
```

realtime (6.1.31-rt11-sun50iw9):
```sh
T: 0 ( 3651) P:80 I:200 C: 173333 Min:      5 Act:    7 Avg:    9 Max:     271
T: 1 ( 3652) P:80 I:200 C: 173298 Min:      5 Act:    8 Avg:    9 Max:     183
T: 2 ( 3653) P:80 I:200 C: 173261 Min:      5 Act:    6 Avg:    8 Max:     275
T: 3 ( 3654) P:80 I:200 C: 173223 Min:      5 Act:    6 Avg:    8 Max:     300
```

default (6.1.31-sun50iw9):
```sh
T: 0 ( 2969) P:80 I:200 C: 116545 Min:      4 Act:   15 Avg:    8 Max:    2807
T: 1 ( 2970) P:80 I:200 C: 116493 Min:      5 Act:   16 Avg:   10 Max:    2588
T: 2 ( 2971) P:80 I:200 C: 116280 Min:      5 Act:   12 Avg:    8 Max:    2886
T: 3 ( 2972) P:80 I:200 C: 116194 Min:      5 Act:   17 Avg:    8 Max:   10533
```
