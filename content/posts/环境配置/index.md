一

```bash
(base) azureuser@VPS-linux:~$ mamba create -n wqb-py3.11 -y python=3.11

Looking for: ['python=3.11']

conda-forge/noarch                                  19.4MB @   5.1MB/s  4.3s
conda-forge/linux-64                                42.4MB @   6.0MB/s  7.9s
Killed
```

二

```bash
(base) azureuser@VPS-linux:~$ mamba create -n wqb-py3.11 -y python=3.11
prefix already exists: /home/azureuser/tools/miniforge3/envs/wqb-py3.11

CondaValueError: prefix already exists: /home/azureuser/tools/miniforge3/envs/wqb-py3.11
(base) azureuser@VPS-linux:~$ mamba create -n wqb-py3.11 -y python=3.11
prefix already exists: /home/azureuser/tools/miniforge3/envs/wqb-py3.11

CondaValueError: prefix already exists: /home/azureuser/tools/miniforge3/envs/wqb-py3.11
```
