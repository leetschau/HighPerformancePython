# High Performance Python

Upstream repo: [high_performance_python_2e](https://github.com/mynameisfiber/high_performance_python_2e)

## Chapter 2

cProfile 能够在 module 级别给出哪些函数（及其中哪些语句）消耗了多少时间，
从而确定需要提升性能的范围。

### Example on p31

```
python -m timeit -n 5 -r 1 -s 'import ex2_5' 'ex2_5.calc_pure_python(desired_width=1000, max_iterations=300)'
```

### Snakeviz on p40

`snakeviz profile.stats` will open a browser to list its graphics.
So you have to run this command on a host with desktop environment.

### py-spy on p54

First get PID of the python process by adding the following lines in Python script:
```
import os
print(os.getpid())
```

Say the PID is 3264553. Run py-spy with:
```
sudo env "PATH=$PATH" py-spy top --pid 3264553
```

### py-spy on p55

The output graph is like that of `snakeviz`, but need root privilege:
```
sudo env "PATH=$PATH" py-spy record -o profile.svg -- python ex2_5.py
```

Speedscope is incompatible with SVG file:
```
sudo env "PATH=$PATH" py-spy record -f speedscope -o profile_speedscope.svg -- python ex2_5.py
```
