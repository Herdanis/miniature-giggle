Provide your CLI command here:

`jq -c '. | select(.symbol == "TSLA" and .side == "sell") | .order_id' transaction-log.txt | xargs -I {} sh -c 'curl -s https://example.com/api/{} >> output.txt'`
