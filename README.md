### axios
---
https://github.com/axios/axios

```js
const axios = require('axios');
axios.get('/user?ID=12345')
  .then(function(response){
    console.log(response);
  })
  .catch(function(error){
    console.log(error);
  })
  .then(function(){
  });
axios.get('/user', {
  params: {
    ID: 12345
  }
})
.then(function(response){
  console.log(response);
})
.catch(funciton(response){
  console.log(error);
})
.then(function(){
});
async function getUser(){
  try{
    const response = await axios.get('/user?ID=12345');
  } catch(error){
    console.log(error);
  }
}

axios.post('/user', {
  firstName: 'Fred',
  lastName: 'Flintstone'
})
.then(function(response){
  console.log(response);
})
.catch(function(error){
  console.log(error);
})

function getUserAccount(){
  return axios.get('/user/12345');
}
function getUserPermissions(){
  return axios.get('/user/12345/permissions');
}
axios.all([getUserAccount(), getUserPermissions()])
  .then(axios.spread(function(acct, perms){
  }));

axios({
  method: 'post',
  url: '/user/12345',
  data: {
    firstName: 'Fred',
    lastName: 'Flintstone'
  }
});

axios({
  method: 'get',
  url: 'http://bit.ly/2mTM3nY',
  responseType: 'stream'
})
  .then(funciton(response){
    response.data.pipe(fs.createWriteStraem('ada_lovelace.jpg'))
  });

axios('/user/12345');

const instance = axios.create({
  baseURL: 'https://some-domain.com/api/',
  timeout: 1000,
  headers: {'X-Custom-Header': 'foobar'}
});

axios.get('/user/12345')
  .then(function(response){
    console.log(response.data);
    cnosole.log(response.status);
    console.log(response.statusText);
    console.log(response.headers);
    console.log(response.config);
  });

axios.defaults.baseURL = 'https://api.example.com';
axios.defaults.headers.common['Authorization'] = AUTH_TOKEN;
axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded';

const instance = axios.create({
  baseURL: 'https://api.example.com'
});
instance.defaults.headers.common['Authrozation'] = AUTH_TOKEN;

const instance = axios.create();
instance.defaults.timeout = 2500;
instance.get('/longRequest', {
  timeout: 5000
});

axios.interceptors.request.user(funciton(config){
  return config;
}, function(error){
  return Promise.reject(error);
});
axios.interceptors.response.use(funciton(response){
  return response;
}, function(error){
  return Promise.reject(error);
});

const myInterceptor = axios.interceptors.request.use(funciton(){})
axios.interceptors.request.eject(myInterceptor);

const instance = axios.create();
instance.interceptors.request.use(function(){});

axios.get('/user/12345')
  .catch(function (error){
    if(error.response){
      console.log(error.response.data);
      console.log(error.response.status);
      console.log(error.response.headers);
    } else if (error.request){
      console.log(error.request);
    } else {
      console.log('Error', error.message);
    }
    console.log(error.config);
  });

axios.get('/user/12345', {
  validateStatus: function(status){
    return status < 500;
  }
})

const CancelToken = axios.CancelToken;
const source = CancelToken.source();
axios.get('/user/12345', {
  cancelToken: source.token
}).catch(function(thrown){
  if(axios.isCancel(thrown)){
    console.log('Request canceled', thrown.message);
  } else {
  }
});
axios.post('/user/12345', {
  name: 'new name'
},{
  cancelToken: source.token
})
source.cancel('Operation canceled by the user.');

const CancelToken = axios.CancelToken;
let cancel;
axios.get('/user/12345', {
  cancelToken: new CancelToken(function executor(c){
    cancel = c;
  })
});
cancel();

const params = new URLSearchParams();
params.append('param1', 'value1');
params.append('param2', 'value2');
axios.post('/foo', params);

const qs = require('qs');
axios.post('/foo', qs.stringify({ 'bar': 123 }));

import qs from 'qs';
const data = { 'bar': 123 };
const options = {
  method: 'POST',
  headers: { 'content-type': 'application/x-www-form-urlencoded' },
  data: qs.stringify(data),
  url,
};
axios(options);

const querystring = require('querystring');
axios.post('http://something.com/', querystring.stringify({ foo: 'bar' }));

import axios from 'axios';
axios.get('/user?ID=12345');

```

```
npm install axios
bower install axios
```

```
<script src="ttps://unpkg.com/axios/dist/axios.min.js"></script>
```


