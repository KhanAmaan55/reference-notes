# Here is how you can create a queue job using the @rlanz/bull-queue package in AdonisJS:

1. Install the package:

```
npm i @rlanz/bull-queue
```

2. Register the provider in `start/app.js`:

```js
const providers = [
  '@rlanz/bull-queue/providers/BullQueueProvider'
]
```

3. Generate a job class: 

```
node ace make:job SendEmail
```

4. Define the job handle method:

```js
async handle() {
  // Job logic
}  
```

5. Dispatch the job:

```js
const { BullQueue } = use('BullQueue')
const SendEmail = use('App/Jobs/SendEmail')

await BullQueue.add(SendEmail.key, {
  // data
}) 
```

6. Configure BullQueue provider in `config/bull-queue.js`:

```js 
connection: {
  host: Env.get('REDIS_HOST'),
  port: Env.get('REDIS_PORT')  
},

queues: ['email']
```

7. Start queue listener:

```
node ace bull:listen --queue=email
```

That covers the basics of setting up a queue & job with @rlanz/bull-queue! Refer to docs for more advanced usage.
