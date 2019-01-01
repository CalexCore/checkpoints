# Checkpoints
### How To Sync Quickly
##### first syncing a new daemon or wallet at fresh chain from 0 may take a long time and will be much quicker by loading "checkpoints" .
##### During syncing  every "older" block hashvalue gets calculated , these hashvalues are in the checkpoints file, 
##### so the cpu does not need to calculate each , rather the daemon needs only to compare with the delivered once.
##### This speeds up syncing especially on lower speed machines. 

### Setup

- Right click [this link](https://github.com/CalexCore/checkpoints/blob/master/checkpoints.csv) and choose `Save link as...` 
and download the latest checkpoints.csv, or use [this link](https://github.com/CalexCore/checkpoints/blob/master/checkpoints.tar.gz) 
to can get a compressed version which may safe some download time, but needs to be extracted.
- You can use "wget" to get the file via commandline on Linux , too. In example use the following syntax 
` wget -O checkpoints.csv https://raw.githubusercontent.com/CalexCore/checkpoints/master/checkpoints.csv `
- Place the checkpoints.csv in the same folder as your AmityCoind daemon
- You can get AmityCoind from here if you don't have it already: [Link](https://github.com/CalexCore/AmityCoin/releases)
- Make sure you shut down any GUI wallets, or any other instances of AmityCoind.

### Usage

#### Windows

- First, open a command prompt in the same directory as AmityCoind.
- This can easily be done by moving to the AmityCoind directory in Windows Explorer, then typing `cmd` in the search bar and hitting enter:

![Opening cmd](https://i.imgur.com/Ua2mfah.jpg)
- Finally, type `AmityCoind.exe --load-checkpoints .\checkpoints.csv` in the command prompt.

#### Linux, Apple

- First, open a command prompt in the same directory as AmityCoind.
- You can use the `cd` command to change to this directory. For example, `cd Downloads/Amity-v0.1.2.346`
- Alternatively, your file manager may provide the ability to open a terminal in your current directory. Navigate to the folder with AmityCoind in, and try right clicking, to see if you can open a terminal there:

![Opening terminal]

- Finally, type `./AmityCoind --load-checkpoints ./checkpoints.csv` in the terminal.

### Expected Output

If you did the steps correctly, you should see something like this output.

```
2018-Dec-22 22:26:06.599862 INFO    Program Working Directory: ./AmityCoind
2018-Dec-22 22:26:06.600025 INFO    Loading Checkpoints for faster initial sync...
2018-Dec-22 22:26:06.615059 INFO    Loaded 33861 checkpoints from ./checkpoints.csv
```

- AmityCoind will then start syncing from checkpoints.
- If you are using the CLI wallet, then you can just wait for it to finish syncing, and open your wallet.
- If you are using a GUI wallet, let it finish syncing, close it down by typing `exit` in the window, then open your GUI wallet.

### Common Errors

#### Invalid checkpoint file format

```
2018-May-13 12:10:08.325056 INFO    Loading Checkpoints for faster initial sync...
2018-May-13 12:10:08.339667 ERROR   Invalid checkpoint file format
2018-May-13 12:10:08.341758 ERROR   Exception: Failed to load checkpoints
```

- If you see output like the above, the file you are opening is either not a .csv file, or hasn't been downloaded correctly.
- Ensure you downloaded the file by right clicking, and choosing `Save link as...`.
- If you incorrectly chose the wrong file, you can accidentally  download a html page instead.
- When you open up the file, it should have lots of lines like this:

```
1,52d34f37a3e2ce48109f2c38116da4101abf0634f256108d574c02a05d8c9085
2,7ad1ec5d6aa83e315cff3a7eaf09cd75973bf6526036e55373dd01c484f5ac99
3,36d78d5c66a184a831f8f00c3e68672ba77ef79e34dedc00df7e34491bd92b63
```

- If you absolutely can't get it working, you can make a new text file, copy all the content from here into it: [Link](https://raw.githubusercontent.com/CalexCore/checkpoints/master/checkpoints.csv)
- Then save as checkpoints.csv (Select filetype: all files in windows)

#### Failed to load checkpoints

```
2018-May-13 12:14:57.544286 INFO    Loading Checkpoints for faster initial sync...
2018-May-13 12:14:57.544569 ERROR   Could not load checkpoints file: checkpoints.csv
2018-May-13 12:14:57.544823 ERROR   Exception: Failed to load checkpoints
```

- If you see output like the above, it means the file isn't present in the directory you are in.
- Make sure you have placed the checkpoints.csv file in the same directory as AmityCoind and check the syntax of the added parameter 
`--load-checkpoints .\checkpoints.csv`
