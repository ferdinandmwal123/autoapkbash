# autoapkbash

LF Line endings (Linux/Unix)

```bash
#! /bin/bash

APK_PATH="$(adb shell pm path $1)"
echo "${APK_PATH#*:}"
APK_PATH=${APK_PATH#*:}

adb pull $(tr -d '\r' <<< "$APK_PATH") "$1.apk"
if [[ -r  "$1.apk" ]]
then
    printf 'OK\n'
else
    printf 'ERROR: %s not found\n' "$base"
    exit 1
fi
#adb pull $APK_PATH
#mv base.apk $1.apk

if [ "$2" == "--jadx" ] || [ "$2" == "-j" ]
    then jadx $1
fi
```

CRLF (Windows Line endings)

```bash
#! /bin/bash

APK_PATH="$(adb shell pm path $1)"
echo "${APK_PATH#*:}"
APK_PATH=${APK_PATH#*:}
adb pull $APK_PATH
mv base.apk $1.apk


if [ "$2" == "--jadx" ] || [ "$2" == "-j" ]
    then jadx $1
fi
```
