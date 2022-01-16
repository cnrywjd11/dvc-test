# dvc-ssh-test
```
➜  dvc-ssh-test git:(master) ls

➜  dvc-ssh-test git:(master) dvc init
Initialized DVC repository.

You can now commit the changes to git.

+---------------------------------------------------------------------+
|                                                                     |
|        DVC has enabled anonymous aggregate usage analytics.         |
|     Read the analytics documentation (and how to opt-out) here:     |
|             <https://dvc.org/doc/user-guide/analytics>              |
|                                                                     |
+---------------------------------------------------------------------+

What's next?
------------
- Check out the documentation: <https://dvc.org/doc>
- Get help and share ideas: <https://dvc.org/chat>
- Star us on GitHub: <https://github.com/iterative/dvc>

➜  dvc-ssh-test git:(master) ✗ ls -a
.          ..         .dvc       .dvcignore .git

➜  dvc-ssh-test git:(master) ✗ mkdir voice-sample

➜  dvc-ssh-test git:(master) ✗ cp ~/Desktop/opus_file/temp/* voice-sample

➜  dvc-ssh-test git:(master) ✗ ls voice-sample/*
voice-sample/EH02_00064_F10A.wav voice-sample/heykakao_hello.wav  voice-sample/kbs-news2.wav       voice-sample/long_sample.mp3     voice-sample/long_sample_8k.wav
voice-sample/EH2.wav             voice-sample/kbs-news.wav        voice-sample/long_20m_34s.wav    voice-sample/long_sample.wav     voice-sample/res.pcm

➜  dvc-ssh-test git:(master) ✗ dvc add voice-sample
100% Adding...|███████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████|1/1 [00:00,  4.42file/s]

To track the changes with git, run:

	git add voice-sample.dvc .gitignore
  
➜  dvc-ssh-test git:(master) ✗ git add voice-sample.dvc .gitignore

➜  dvc-ssh-test git:(master) ✗ cat voice-sample.dvc
outs:
- md5: c432f77c2a131ea5201e83613bdc3b7c.dir
  size: 234042815
  nfiles: 10
  path: voice-sample
  
➜  dvc-ssh-test git:(master) ✗ git commit -m "add voice-sample.dvc"
[master (최상위-커밋) f04267a] add voice-sample.dvc
 11 files changed, 521 insertions(+)
 create mode 100644 .dvc/.gitignore
 create mode 100644 .dvc/config
 create mode 100644 .dvc/plots/confusion.json
 create mode 100644 .dvc/plots/confusion_normalized.json
 create mode 100644 .dvc/plots/default.json
 create mode 100644 .dvc/plots/linear.json
 create mode 100644 .dvc/plots/scatter.json
 create mode 100644 .dvc/plots/smooth.json
 create mode 100644 .dvcignore
 create mode 100644 .gitignore
 create mode 100644 voice-sample.dvc
 
➜  dvc-ssh-test git:(master) dvc remote add -d dvc-ssh-test ssh://{ip}/home/ubuntu/dvc-ssh-test-dir
Setting 'dvc-ssh-test' as a default remote.

➜  dvc-ssh-test git:(master) ✗ dvc remote modify dvc-ssh-test user ubuntu

➜  dvc-ssh-test git:(master) ✗ dvc remote modify dvc-ssh-test port 22

➜  dvc-ssh-test git:(master) ✗ dvc remote modify dvc-ssh-test keyfile {private_key.pem path}

➜  dvc-ssh-test git:(master) ✗ cat .dvc/config
[core]
    remote = dvc-ssh-test
['remote "dvc-ssh-test"']
    url = ssh://{ip}/home/ubuntu/dvc-ssh-test-dir
    user = ubuntu
    port = 22
    keyfile = {private_key.pem path}
  
➜  dvc-ssh-test git:(master) ✗ git add .dvc/config

➜  dvc-ssh-test git:(master) ✗ git commit -m "add remote storage(ssh)"
[master 31f6e5b] add remote storage(ssh)
 1 file changed, 7 insertions(+)
 
➜  dvc-ssh-test git:(master) dvc push
10 files pushed

```

