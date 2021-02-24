# Checkpoints
# How To Sync your Blockchain Quickly
# Sync a new chain from 0 by loading  checkpoints with your daemon.

# Setup

- Right click [this link] https://github.com/QbitNetwork/checkpoints.csv choose the raw button click and `Save link as...` to download the latest checkpoints.csv.
- Place checkpoints.csv in the same folder as your QbitNetworkd daemon normally src directory
- You can get QbitNetworkd from here if you don't have it already: https://github.com/QbitNetwork/Qbit.git
- Make sure you shut down any GUI wallets, or any other instances of QbitNetworkd.

  <a href="https://t.me/Qbitcurrency">Help is available on Telegram </a>


# Linux, Apple

- First, open a command prompt in the same directory as QbitNetworkd.
- You can use the `cd` command to change to this directory.  cd Qbit/build/src   You should find QbitNetworkd in this directory
- Alternatively, your file manager may be able to open a terminal in your current directory. Navigate to the folder with QbitNetworkd in, and try right clicking, to see if you can open a terminal there:
-Add checkpoints.csv to src; As you can see checkpoints.csv and QbitNetworkd are both in this directory.

![Finding QbitNetworkd] <img src="https://github.com/QbitNetwork/checkpoints.csv/blob/main/Screenshot_29.png" alt="Qbit screenshot">

- Finally, type ./QbitNetworkd --load-checkpoints checkpoints.csv  in the terminal.<br>

 You may also add:  ./QbitNetworkd  --load-checkpoints checkpoints.csv --enable-blockexplorer --enable-cors="*" --rpc-bind-ip=0.0.0.0 --rpc-bind-port=20101 --fee-amount 10 --fee-address QBC9V3fD5orFayFPLDYxbhVD2m2ZamJL81XRde1iKa4eHFyEvkzeTy541QwB8RTKzz1sy6pFouk7K8fxBkcqkSw44BiBPBSYms

# Expected Output

If your steps were correct, you should see something like the output below.

```
2021-Feb-24 17:47:54.941849 INFO    Program Working Directory: "/home/seed3/Qbit/build/src"
2021-Feb-24 17:47:54.941949 INFO    Loading Checkpoints for faster initial sync...
2021-Feb-24 17:47:54.941991 INFO    Loaded 7 checkpoints from checkpoints.csv       < This  is the checkpoints.csv Loading as seen here >
2021-Feb-24 17:47:54.942031 INFO    Opening DB in /home/seed3/.Qbit/DB
2021-Feb-24 17:47:55.025355 INFO    DB opened in /home/seed3/.Qbit/DB
2021-Feb-24 17:47:55.025663 INFO    Initializing core...
2021-Feb-24 17:47:55.027406 INFO    Core initialized OK
2021-Feb-24 17:47:55.028441 INFO    Initializing p2p server...
2021-Feb-24 17:47:55.028813 INFO    Binding on 0.0.0.0:20100
2021-Feb-24 17:47:55.028869 INFO    Net service bound on 0.0.0.0:20100
2021-Feb-24 17:47:55.028891 INFO    Attempting to add IGD port mapping.
2021-Feb-24 17:47:59.034088 INFO    No IGD was found.
2021-Feb-24 17:47:59.034194 INFO    P2p server initialized OK
2021-Feb-24 17:47:59.034231 INFO    Starting core rpc server on address 0.0.0.0:20101
2021-Feb-24 17:47:59.034555 INFO    Starting p2p net loop...
2021-Feb-24 17:47:59.034591 INFO    Starting node_server

```

- QbitNetworkd will then start syncing from checkpoints.
--IMPORTANT
- Please Remember to type EXIT when closing your CLI wallet to save the data.
- If you are using the CLI wallet, then you can wait for it to finish syncing, and open your wallet.


# Common Errors

# Invalid checkpoint file format

```
2021-Feb-13 12:10:08.325056 INFO    Loading Checkpoints for faster initial sync...
2021-Feb-13 12:10:08.339667 ERROR   Invalid checkpoint file format
2021-Feb-13 12:10:08.341758 ERROR   Exception: Failed to load checkpoints
```

- If you see output like this the file you are opening is either not a .csv file, or hasn't been downloaded correctly.
- Ensure you downloaded the file by right clicking, and choosing `Save link as...`.
- If you incorrectly chose the wrong file, you can accidentally  download a html page instead.
- When you open up the file, it should have lots of lines like this:

```
100,d5389a48784e8bd4dc05ff908513a66ceddc38ae2370779a203431ada1e59699
200,0384a120dc1ab34f1cb2ace63066fb915e0d73c3815d632c162a523a012ce42f
300,5fa3819a54429a878375d15467f03e701256d33f2a359ebb45db8ad9b993bbd1
400,8019ce6c8a44d348853ab92d5f4fbe967b690ba7db8c5d07a70f9504b7075c99
```

- If you can't get it working, Go make a new text file, copy the content from this raw file into it: https://raw.githubusercontent.com/QbitNetwork/checkpoints.csv/main/checkpoints.csv
- Then save the file as checkpoints.csv ( This is=> Select filetype: all files in windows) make sure when its added to SRC Directory that it ends correctly as .csv

# If we Failed to load the checkpoints

```
2021-Feb-13 17:20:34.254963 INFO    Loading Checkpoints for faster initial sync...
2021-Feb-13 17:20:34.254967 ERROR   Could not load checkpoints file: checkpoints.csv
2021-Feb-13 17:20:34.255033 ERROR   Exception: Failed to load checkpoints
```

- If you see output like the above, it means the file isn't present in the directory you are in.
- Make sure you have placed the checkpoints.csv file in the same directory as QbitNetworkd.

# QbitNetworkd.exe is not recognized / No such file or directory

```
C:\Users\gentoo>QbitNetworkd.exe --load-checkpoints checkpoints.csv
'QbitNetworkd.exe' is not recognized as an internal or external command,
operable program or batch file.
```

`bash: ./QbitNetworkd: No such file or directory`

- If you see output like one of the above, it means your terminal isn't in the same folder as the QbitNetworkd program.
- You can type `pwd` to see what folder you are currently in.
- Try following the steps above to get into the right folder, then try again.
- If you type `ls`, you should see the QbitNetworkd program, if you are in the correct folder:

```
[QbitNetworkd] ls
seed3@vmi419579:~/Qbit/build/src$ ls
checkpoints.csv      libCommon.a          libErrors.a   libMnemonics.a  libSerialization.a  libWalletBackend.a  Q-service
CMakeFiles           libConfig.a          libHttp.a     libNigel.a      libSubWallets.a     Makefile            zodiac
cmake_install.cmake  libCrypto.a          libLogger.a   libP2P.a        libSystem.a         miner
cryptotest           libCryptoNoteCore.a  libLogging.a  libRpc.a        libUtilities.a      QbitNetworkd

```

# IO error

```
2021-Feb-13 11:58:40.657053 INFO    Opening DB in /home/Your_User/.Qbit/DB
2021-Feb-13 11:58:40.658171 ERROR   DB Error. DB can't be opened in /home/Your_User/.Qbit/DB. Error: IO error: While lock file: /home/Your_User/.Qbit/DB/LOCK: Resource temporarily unavailable
2021-Feb-13 11:58:40.673686 ERROR   Exception: IO error
```

- If you see output like the above, something else has the database open already.
- Make sure you have closed down any other QbitNetworkd's, GUI wallets, and walletd.
- Use a task manager to help you find any which might be running in the background, then try again.
