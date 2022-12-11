# Managing-Archiving-and-Tar-in-RedHat-Linux

## What is tar? 

Archiving and compressing files are useful when creating backups and transferring data across a network. One of the oldest and most common commands for creating and working with backup archives is the tar command.

With tar, users can gather large sets of files into a single file (archive). The archive can be compressed using gzip, bzip2, or xz compression.

### Note 
```
A leading hyphen(-) is not required for tar options. 
```
## Archive files and directories with tar

Before creating a tar archive, verify that there is no other archive in the directory with the same name as the new archive to be created. The tar command will overwrite an existing archive without any feedback. 

The first option to use when creating a new archive is the c option, followed by the f option, then a single space, then the file name of the archive to be created, and finally the list of files and directories that should get added to the archive. The archive is created in the current directory unless specified otherwise.
```
	#tar  cf  archive file name list of files
	#tar  cf  archive.tar file1 file2 file3....filen
	#tar  cf  archive file name list of files
	#tar  cf  archive.tar file1 file2 file3....filen
```
### Tar Command:

Options:

- c	--create = create new archive
- x 	--extract = extract from existing archive
- t 	--list = list table of contents
- v  	--verbose = show files 
- f 	--file = file name
- p	--preserve-permissions
- x	--tar, filename.tar
- z 	--gzip, filename.tar.gz
- j	--bzip2, filename.tar.bz2
- J	--xz, filename.tar.xz

### To create a compressed tar archive, one of the following tar options can be specified: 

- z for gzip --compression (filename.tar.gz or filename.tgz) 
- j for bzip2 --compression (filename.tar.bz2) 
- J for xz --compression (filename.tar.xz)


A tar archive should normally be extracted in an empty directory to ensure it does not overwrite any existing files. If files are extracted by root, tar attempts to preserve the original user and group ownership of the files. If a regular user extracts files using tar, the extracted files are 
owned by that user.

#### To create tar compressed file:
```
	#tar  cf  file name.tar file list /#tar -cf file name.tar file list
	#tar  cf  tarfile.tar file1 file2 file3 file4.....fileN
```
#### To create gzip compressed file:
```
  #tar czf file name.tar.gz or file name.tgz file list                     
  #tar czf gzipfile.tar.gz or gzipfile.tgz  file1 file2 file3 file4.....fileN
```
#### To create bzip2 compressed file:
```
	#tar cjf file name.tar.bz2 file list / #tar -cjf file name.tar.bz2 file list
	#tar cf bzipfile.bz2 file1 file2 file3 file4.....fileN
```
#### To create xz compressed file:
```
	#tar cJf file name.xz file list  /#tar -cJf file name.xz file list
	#tar cJf xzfile.xz file1 file2 file3 file4.....fileN
```



## Extract compressed file:

#### Extract tar file:
```
  #tar xf tar file name or file path  / #tar -xf tar file name or file path
  #tar xf tarfile.tar
  #tar xf /home/sifat/tarfile.tar
```
#### Extract gzip file:
```
  #tar xzf file name or file path / #tar -xzf file name or file path
  #tar xzf gzipfile.tar.gz
  #tar xzf /home/sifat/gzipfile.tar.gz
```
#### Extract bzip2 file:
```
  #tar xjf file name or file path / #tar -xjf file name or file path
  #tar xzf bzip2file.tar.bz2
  #tar xzf /home/sifat/bzip2file.tar.bz2
```
#### Extract xz file:
```
  #tar xJf file name or file path / #tar -xJf file name or file path
  #tar xzf xzfile.tar.xz
  #tar xzf /home/sifat/xzfile.tar.xz
```
#### To show file list under compressed file:
```
  #tar tf file name or file path / #tar -tf file name or file path
  #tar tf tarfile.tar
  #tar tf /home/sifat/gzipfile.tar.gz
```
## Preserve Permission

By default, when files get extracted from an archive, the umask is subtracted from the permissions of archive content. This is a security measure and prevents extracted regular files from receiving execute permissions by default. To preserve the permissions of an archived file, the p option is to be used when extracting an archive.

	
          #tar xpf file name or file path
          #tar xjpf file name or file path



### Verbose

Verbose (v) option used to show which files get archived or extracted. 

#### Create compressed file:
```
[root@redhatsifat tar3]# tar cjvf file.tar.bz2 file1 file2 file3 file4
file1
file2
file3
file4
[root@redhatsifat tar3]#
```
#### Extract file:
```
[root@redhatsifat tar]# tar xjvf /tar/bz2.tar.bz2
file1
file2
file3
file4
[root@redhatsifat tar]#
```
## gzip, bzip2, and xz

Create a compressed tar archive There are three different compression methods supported by the tar command. The gzip compression is the fastest and oldest one, and is most widely available. The bzip2 compression usually leads to smaller archive files compared to gzip and is less widely available than gzip, while the xz compression method is relatively new, but usually offers the best compression ratio of the methods available. 


#### Additionally, gzip, bzip2, and xz can be used independently to compress single files. For example,

- #gzip  abc.tar results in the compressed file  abc.tar.gz 
- #bzip2  abc.tar results in the compressed file  abc.tar.bz2 
- #xz  abc.tar results in the compressed file  abc.tar. xz. 

#### The corresponding decompress commands are gunzip, bunzip2, and unxz. For example, 

- #gunzip abc.tar.gz results in the uncompressed tar file abc.tar
- #bunzip2 abc.tar.bz2 results in the uncompressed tar file abc.tar 
- #unxz abc.tar.xz results in the uncompressed tar file abc.tar.

 ## SSH    


The ssh command is useful for securely running shell commands on remote systems. It can also be used to securely copy files from one machine to another.

1. First you check ssh service /port ON or OFF in your linux and windows system
* Check Linux machine:
```
	#[root@redhatsifat ~]# ss -ta
State   Recv-Q   Send-Q       Local Address:Port            Peer Address:Port
LISTEN  0        128                0.0.0.0:sunrpc               0.0.0.0:*
LISTEN  0        32           192.168.122.1:domain               0.0.0.0:*
LISTEN  0        128                0.0.0.0:ssh                  0.0.0.0:*
LISTEN  0        5                127.0.0.1:ipp                  0.0.0.0:*
LISTEN  0        5                127.0.0.1:44321                0.0.0.0:*
LISTEN  0        5                127.0.0.1:dey-sapi             0.0.0.0:*
ESTAB   0        64           192.168.10.10:ssh            192.168.10.12:6542
LISTEN  0        128                   [::]:sunrpc                  [::]:*
LISTEN  0        128                   [::]:ssh                     [::]:*
LISTEN  0        5                    [::1]:ipp                     [::]:*
LISTEN  0        5                    [::1]:44321                   [::]:*
LISTEN  0        128                      *:websm                      *:*
LISTEN  0        5                    [::1]:dey-sapi                [::]:*
[root@redhatsifat ~]#
```
If you see the ssh service port LISTEN or ESTAB State , It means ssh service is ON. Otherwise you have to follow steps 2. 

* Check windows machine:
```
	C:\Users\sifat>telnet 192.168.10.12 22    [where 192.168.10.12 is windows ip address and 22 is the ssh port number]

	‘SSH-2.0-OpenSSH_for_Windows_7.7’
```
If you see avobe message then your windows ssh service is ON.Otherwise you have to follow steps 3.

2. Install ssh service package From yum or RPM package management.

3. Install OpenSSH Server and OpenSSH Client then start OpenSSH server

## Installation Process

```
  1. Go to windows setting option
  2. Click Apps option 
  3. Click optional features option
  4. Search OpenSSH Server and Install it.
  5. Again Search OpenSSH Client and Install it.
```
## Start SSH server:
```
  1. Go to the Windows search bar.
  2. Search services.
  3. Click service.
  4. Find OpenSSH service.
  5. Right click and go to properties.
  6. startup type : select Automatic.
  7. then click the ok button and click the apply button.
  8. Now click start.
```

## SCP 

 Securely Copy file one machine to another.

#### File copy from remote machine to local machine:
```
  #scp remote machine username@ip address:file name or file path   local machine file location path
  #scp sifat@192.168.10.12:C:user/sifat/file4  /home/sifat/a
```
#### Directory Copy from remote machine to local machine:
```
  #scp -r remote machine username@ip address:directory name or directory path   local machine directory location path   [ r for recursive ]
  #scp -r sifat@192.168.10.12:C:user/sifat/Downloads  /home/sifat/a
```
#### File copy from local machine to remote machine:
```
  #scp file name or file path remote machine username@ip address:remote machine file location path
  #scp /home/sifat/b  sifat@192.168.10.12:C:\users\sifat
```
#### Directory copy from local machine to remote machine:
```
  #scp -r directory name or directory path remote machine username@ip address:remote machine file location path
  #scp -r /home/sifat/b  sifat@192.168.10.12:C:\users\sifat
```
## SFTP

SFTP means Securely File Transfer Protocol

#### How to Connect to SFTP 

To start an SFTP session, enter the username and remote hostname or IP address at the command prompt.
Once authentication is successful, you will see a shell with an sftp> prompt.
```
  #sftp Remote machine UserName@IP address or remote HostName
  #sftp sifat@192.168.10.12
```
```
  [root@tecmint ~]# sftp tecmint@27.48.137.6

  Connecting to 27.48.137.6...
  tecmint@27.48.137.6's password:
sftp>
```
#### Upload or Send single file local machine to remote machine:
```
  sftp>put FileName or Path
  sftp>put file1
```
#### Upload or Send multiple files local machine to remote machine:
```
  sftp>put FileName or Path*
  sftp>put file*.taxt
```
#### Download or get single file from remote machine to local machine:
```
  sftp>get FileName or Path
  sftp>get file1
```
#### Download or get multiple files from remote machine to local machine:
```
  sftp>mget FileName or Path*
  sftp>mget file*.taxt
```
### Check Present Working Directory

The command ‘lpwd‘ is used to check the Local present working directory, 
whereas ‘pwd‘ command is used to check Remote working directory.
```
  sftp> lpwd
```
Local working directory: /
```
  sftp> pwd
```
Remote working directory: /tecmint/
```
  lpwd – print the current directory on your system
  pwd – print the current directory on the ftp server
```
#### Listing Files

Listing files and directories in local as well as remote system.

  On Remote
```
  sftp> ls
```
 On Local
```
  sftp> lls
```

#### mkdir, cd,rm etc commands run for remote machine .
If you run these command for local machine, you have to add 'l'
```
 Example:

Remote machine		Local Machine

	#ls			#lls
	#ll			#lll
	#pwd			#lpwd
	#mkdir		#lmkdir
	#cd			#lcd
	#rm for file
	#rmdir for derectory
			
		etc

```

Example
```
cd sourcelogs/
  636  ls
  637  vim log 
  638  crontab -l
  639  crontab -e
  640  crontab -l
  641  cd /home/sifat/sourcelogs/
  642  ls
  643  echo "Logs at 1:33PM " >> log3
  644  ls
  645  vim log3
  646  rsync -av /home/sifat/sourcelogs/ sifat@192.168.10.12:
  647  sifat
  648  rsync -av /home/sifat/sourcelogs/ sifat@192.168.10.12: -p sifat
  649  rsync -av /home/sifat/sourcelogs/ sifat@192.168.10.12:
  650  crontab -l
  651  ls
  652  pwd
  653  history
  654  scp sifat@192.168.10.12:C:\Users\sifat\file1  /home/sifat
  655  pwd
  656  cd /home/sifat/
  657  ls
  658  ll
  659  scp sifat@192.168.10.12:C:\Users\sifat\*  /home/sifat/
  660  ls
  661  ll
  662  ls
  663  iptables -L
  664  iptables -F
  665  iptables -L
  666  scp sifat@192.168.10.12:C:\Users\sifat\*  /home/sifat/
  667  ls
  668  scp -r sifat@192.168.10.12:C:\Users\sifat\*  /home/sifat/
  669  ls
  670  cat /var/log/secure
  671  ip a
  672  pwd
  673  sftp
  674  sftp 192.168.10.12
  675  ssh 192.168.10.12
  676  sftp sifat@192.168.10.12
  677  scp sifat@192.168.10.12:C:/Users/sifat/file2 /home/sifat/file2
  678  ls
  679  scp sifat@192.168.10.12:C:/Users/sifat/file2 /home/sifat/
  680  scp sifat@192.168.10.12:C:/Users/sifat/file3 /home/sifat/
  681  ls
  682  scp -r sifat@192.168.10.12:C:/Users/sifat/file3 /home/sifat/
  683  ls
  684  scp -r sifat@192.168.10.12:C:/Users/sifat/* /home/sifat/
  685  ls
  686  cd Downloads/
  687  ls
  688  cd ..
  689  cat /var/logs
  690  ls logs
  691  cd /var/logs
  692  cat /var/logs
  693  cd /var
  694  ls
  695  cd logs
  696  cd log
  697  ls
  698  cat secure
  699  ls
  700  cd /home/sifat
  701  ls
  702  mkdir sourcelogs
  703  cd sourcelogs/
  704  echo "log fiels at 11:07AM" >>log
  705  ls
  706  cat log 
  707  cd ..
  708  cd /tmp
  709  ls
  710  mkdir syncfolder
  711  rsync -av /home/sifat/sourcelogs/ /tmp/syncfolder/
  712  ls
  713  cd syncfolder/
  714  ls
  715  cat log 
  716  ls
  717  cat log 
  718  rsync -av /home/sifat/sourcelogs/ /tmp/syncfolder/
  719  ls
  720  cat log 
  721  #rsync -av /home/sifat/sourcelogs/ /tmp/syncfolder/
  722  pwd
  723  cd ~
  724  pwd
  725  echo "rsync -av /home/sifat/sourcelogs/ /tmp/syncfolder/" >> filesync.sh
  726  ls
  727  cat filesync.sh 
  728  pwd
  729  ls
  730  pwd
  731  cd /home/sifat/sourcelogs/
  732  ls
  733  echo " logs generated at 1:24 PM" >>log2
  734  ls
  735  vim log
  736  ls
  737  cd /tmp/syncfolder/
  738  ls
  739  systemctl restart  crontab
  740  crontab -e
  741  /root/filesync.sh
  742  chmod 777 /root/filesync.sh 
  743  /root/filesync.sh
  744  ls
  745  cat log2
  746  cat /var/log/cron
  747  systemctl start crond.service
  748  systemctl status crond.service
  749  ls
  750  chkconfig --list
  751  chkconfig -list
  752  ls
  753  cat log3
  754  cd /root/
  755  ls
  756  vim filesync.sh 
```
### Thank You

##### If you have any feedback, please reach out to me at mdsifathossain100@gmail.com
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/md-sifat-hossain-461274184/)
[![twitter](https://img.shields.io/badge/twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/ict_all)

[@sifat](https://github.com/MdsifatHossain)
