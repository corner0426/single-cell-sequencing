# Cell Ranger Installation

## Download and install

Download files from [downloads page](
https://support.10xgenomics.com/single-cell-gene-expression/software/downloads/latest)

```shell
# unpacks Cell Ranger, its dependencies, and the cellranger script

tar -xzvf cellranger-3.0.2.tar.gz
```

## Prepend the Cell Ranger directory to  $PATH
```shell
vi ~/.bashrc


export PATH=/home/yaoyh/software/cellranger-3.0.2:$PATH
```

`重启shell后生效`

## Verify Installation

```shell
cellranger testrun --id=tiny
```