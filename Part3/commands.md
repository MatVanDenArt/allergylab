docker network create pubsub-net
docker run -d --rm --name redis-server --network=pubsub-net -p 6379:6379 redis

docker build -t 104interactive .

# Subscriber
docker run -it --network=pubsub-net --name subscriber 104interactive

import redis, time
r = redis.Redis(host='redis-server', port=6379, db=0)
p = r.pubsub()
p.subscribe("food_info")
while True:
    message = p.get_message()
    if message:
        print(message)
        print(message['data'])
    time.sleep(0.01)

# Publisher
docker run -it --rm --name publisher --network=pubsub-net 104interactive

import redis
r = redis.Redis(host='redis-server', port=6379, db=0)

r.publish('food_info', 'Ham Sandwich')