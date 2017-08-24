# Shell

## Snippets

```sh
#!/bin/bash

SCRIPT_DIR="$(readlink -f $(dirname $0))"

usage() {
cat <<-EOH
  $0 [-a <aws_profile>] [-r <aws_region>] <template files... or directory>

  options:
    -a: using aws profile
    -r: using aws region
EOH
}

while getopts a:r: OPT
do
  case $OPT in
    a)
      aws_profile="$OPTARG"
      ;;
    r)
      aws_region="$OPTARG"
      ;;
    *)
      usage
      exit 1
      ;;
  esac
done
shift $((OPTIND - 1))
```

## Trap

```
trap "cmd" SIGNAL
```

signalの種類は `kill -l` とか `kill -t` とか。  
Macだと `kill -t` で Ubuntu だと `kill -l` っぽい。

```
$ gkill -t
 1 HUP    Hangup: 1
 2 INT    Interrupt: 2
 3 QUIT   Quit: 3
 4 ILL    Illegal instruction: 4
 5 TRAP   Trace/BPT trap: 5
 6 ABRT   Abort trap: 6
 7 EMT    EMT trap: 7
 8 FPE    Floating point exception: 8
 9 KILL   Killed: 9
10 BUS    Bus error: 10
11 SEGV   Segmentation fault: 11
12 SYS    Bad system call: 12
13 PIPE   Broken pipe: 13
14 ALRM   Alarm clock: 14
15 TERM   Terminated: 15
16 URG    Urgent I/O condition: 16
17 STOP   Suspended (signal): 17
18 TSTP   Suspended: 18
19 CONT   Continued: 19
20 CHLD   Child exited: 20
21 TTIN   Stopped (tty input): 21
22 TTOU   Stopped (tty output): 22
23 IO     I/O possible: 23
24 XCPU   Cputime limit exceeded: 24
25 XFSZ   Filesize limit exceeded: 25
26 VTALRM Virtual timer expired: 26
27 PROF   Profiling timer expired: 27
28 WINCH  Window size changes: 28
29 INFO   Information request: 29
30 USR1   User defined signal 1: 30
31 USR2   User defined signal 2: 31
```

### Example

シェルスクリプトが、形はどうあれ終了した時に tmp ファイルを削除。  
EXIT や ERR は 疑似シグナル。シェルスクリプトが終了した時、エラーが発生した時に発火する。

```
trap "[ -f /tmp/hoge ] && rm /tmp/hoge" SIGINT SIGQUIT SIGKILL SIGTERM EXIT ERR
```



