



# common-http请求方法

### 安装方法

```bash
npm install jimmy-common-http
```

### http使用方法

```javascript
import http from 'common-http';
import env from './env';
import utils from '@/public/utils.js';

/**
 * url: 地址
 * method: 请求方法
 * params: 参数
 * timeout: 超时时间
 * isOriginalGET: 是否传统get传参
 */

// 接口错误提示
const errorCallback = (info) => {
    utils.failTip(info);
}

const req = ({ baseUrl, method, url, params, timeout, isOriginalGET}) => {
    let options={
        url: env[baseUrl] + url,
        method: method, 
        params: params, 
        timeout: timeout, 
        isOriginalGET: isOriginalGET,
        errorCallback:errorCallback
    };
    return http(options);
}

export default req;
```

### 参数说明

| 参数          | 说明                   | 类型     | 默认值 | 备注                                |
| :------------ | ---------------------- | -------- | ------ | ----------------------------------- |
| url           | (必填)api地址          | String   | -      | -                                   |
| method        | (必填)请求方法         | String   | -      | get/post/put/delete                 |
| params        | (必填)请求参数         | Object   | -      | -                                   |
| timeout       | 超时时间               | Number   | 20000  | -                                   |
| extraConfig   | 额外axios配置项        | Object   | -      | -                                   |
| isOriginalGET | 是否传统get传参        | Boolean  | false  | 使用url/?xxx=yyy的方法传参          |
| errorCallback | (必填)错误信息回调处理 | Function | -      | function(info) 回调提示显示info内容 |