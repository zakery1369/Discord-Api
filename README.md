# Discord-Api
Discord Api Bot

## For Send Message in Channel With Webhook
Edit Channel --> Integrations --> Webhooks --> New Webhook --> Copy Webhook URL
```
curl -H "Content-Type: application/json" -X POST $webhook_url \
-d "{\"content\":\"$message\"}"
```
# For Send Message in Channel With Your Bot
```
curl -H "Authorization: Bot $bot_token" -H "Content-Type: application/json" -X POST \
-d "{\"content\":\"$message\"}" "https://discord.com/api/v9/channels/$channel_id/messages"
```
# For Send Direct Message To Other Users With Your Bot
```
DM_ID=$(curl -H "Authorization: Bot $bot_token" -H "Content-Type: application/json" \
-X POST -d "{\"recipient_id\": \"$user_id\"}" \
"https://discord.com/api/v9/users/@me/channels" | sed -n 's/.*"id":"\([^"]*\)".*"type":1.*/\1/p')
curl -H "Authorization: Bot $bot_token" -H "Content-Type: application/json" \
-X POST -d "{\"content\":\"$message\"}" "https://discord.com/api/v9/channels/$DM_ID/messages"
```
