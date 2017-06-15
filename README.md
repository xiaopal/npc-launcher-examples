```
for I in {1..5};do 
  docker run --rm \
    -e NPC_SERVICE=zookeeper.$I \
	-e ZK_PORT=18011 \
	-e NPC_BOOTSTRAP_ONCE=Y \
	-e NPC_BOOTSTRAP_EXPECT=5 \
	xiaopal/npc-bootstrap:latest \
	jq -r '"\(.tags.service)=\(.addr):\(env.ZK_PORT)"' bootstrap.servers &
done
```