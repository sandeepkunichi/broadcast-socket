# broadcast-socket
A simple Node.js ws server that broadcasts events to all clients.

## Runbook

### Deployment
To run the server locally
```
$ npm start
```
This starts up the server on http://localhost:3000

To deploy to heroku
```
$ heroku create
$ git commit -am "version 1.0"
$ git push heroku master
```
This starts up the server on https://broadcast-socket.herokuapp.com

### Sample Client
You can have a `sender` client in JavaScript that looks like this:
```
ws = new WebSocket('wss://broadcast-socket.herokuapp.com');
ws.onopen = () => {
  console.log('connected');
};
ws.onclose = () => {
  console.log('disconnected');
};
ws.send('Hello world!');
```

A receiver client would look like this:
```
ws = new WebSocket('wss://broadcast-socket.herokuapp.com');
ws.onopen = () => {
  console.log('connected');
};
ws.onclose = () => {
  console.log('disconnected');
};
ws.onmessage = event => {
  console.log(event.data);
};
```
