# Data

## Train

Traning dataset uses Reddit data from year 2011 to 2012. It can be built with [this script](https://github.com/golsun/DialogRPT/blob/master/data.sh), which downloads raw data from [a third party dump](https://files.pushshift.io/reddit) and extract comparable pairs of comments for classification tasks. 
```bash
git clone https://github.com/golsun/DialogRPT
cd DialogRPT
sh data.sh
```
See [expected file structure](./data/file_structure.md) of the `data` folder. 

And the table shows some basic statistics.

|   Task  | Training size |
| :------:| :---:|
| `updown`| 40.7 M
| `width` | 22.3 M |
| `depth` | 25.1 M |


## Test
Testing data uses Reddit data from year 2013 and can be downloaded [here](https://xiagnlp2.blob.core.windows.net/dialogrpt/test.zip) or use the command below
```
wget https://xiagnlp2.blob.core.windows.net/dialogrpt/test.zip
unzip test.zip
```
See [evaluation](https://github.com/golsun/DialogRPT#evaluation) to reproduce the results of [DialogRPT](https://github.com/golsun/DialogRPT) performance.
