# Example stuff

Used examples [From here](https://www.freecodecamp.org/news/crack-passwords-using-john-the-ripper-pentesting-tutorial/)

```bash
john --single --format=raw-sha1 crack.txt
```

Cleanup the john.pot file if you want to see output for already cracked hashes

```bash
rm /john/run/john.pot
```

Crack from a wordlist

```bash
john --wordlist=/workspace/examplelist.txt --format=raw-sha1 crack.txt
```
