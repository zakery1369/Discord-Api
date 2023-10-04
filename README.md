# Discord-Api
![Discord-Bot-Api](https://raw.githubusercontent.com/zakery1369/pics/master/Discord-Bot-Api.png)

### For Send Message in Channel With Webhook
Edit Channel --> Integrations --> Webhooks --> New Webhook --> Copy Webhook URL

```
curl -H "Content-Type: application/json" -X POST $webhook_url \
-d "{\"content\":\"$message\"}"
```


### For Send Message in Channel With Your Bot

```
curl -H "Authorization: Bot $bot_token" -H "Content-Type: application/json" -X POST \
-d "{\"content\":\"$message\"}" "https://discord.com/api/v9/channels/$channel_id/messages"
```

### For Send Direct Message To Other Users With Your Bot

```
DM_ID=$(curl -H "Authorization: Bot $bot_token" -H "Content-Type: application/json" \
-X POST -d "{\"recipient_id\": \"$user_id\"}" \
"https://discord.com/api/v9/users/@me/channels" | sed -n 's/.*"id":"\([^"]*\)".*"type":1.*/\1/p')

curl -H "Authorization: Bot $bot_token" -H "Content-Type: application/json" \
-X POST -d "{\"content\":\"$message\"}" "https://discord.com/api/v9/channels/$DM_ID/messages"
```

### For Send Message And File in Channel With Webhook
Edit Channel --> Integrations --> Webhooks --> New Webhook --> Copy Webhook URL

```
curl -X POST -H "Content-Type: multipart/form-data" -F "file=@/home/zakzaki/Desktop/images.png" \
-F "content=$message" $webhook_url
```

### For Send Message And File in Channel With Your Bot

```
curl -X POST -H "Content-Type: multipart/form-data" -F "file=@/home/zakzaki/Desktop/images.png" \
-F "content=$message" -H "Authorization: Bot $bot_token" "https://discord.com/api/v9/channels/$channel_id/messages"
```

### For Send Direct Message And File To Other Users With Your Bot

```
DM_ID=$(curl -H "Authorization: Bot $bot_token" -H "Content-Type: application/json" \
-X POST -d "{\"recipient_id\": \"$user_id\"}" \
"https://discord.com/api/v9/users/@me/channels" | sed -n 's/.*"id":"\([^"]*\)".*"type":1.*/\1/p')

curl -X POST -H "Content-Type: multipart/form-data" -F "file=@/home/zakzaki/Desktop/images.png" \
-F "content=$message" -H "Authorization: Bot $bot_token" "https://discord.com/api/v9/channels/$DM_ID/messages"
```
