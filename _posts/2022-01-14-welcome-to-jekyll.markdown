---
layout: post
title: "Using Azure IoT Central API with React"
date: 2022-01-14 10:52:06 +0900
categories: Azure IoT Central React
---

# 1. Setting '.env' file

## Set value

- Setting Host API
- Setting Authorization
  ![env setting](../_assets/env_setting.png)

## Caution

- REACT_APP must be included in the variable name.

# 2. Make apiConfig file

- 'Axios' is an HTTP asynchronous communication library that utilizes the Promise API for browsers and Node.js.
- You can use 'Fetch'

```javascript
import axios from "axios";
```

- Declare the API and auth token set in .env file.

```javascript
const apiEndpoint = process.env.REACT_APP_FUNCTION_CENTRAL_ENDPOINT;
const apiToken = process.env.REACT_APP_FUNCTION_CENTRAL_TOKEN;
```

- Write a function that retrieves a value using the API

```javascript
const getMonitorData = async (param) => {
  const config = {
    method: "GET",
    data: JSON.stringify(param),
    headers: {
      Authorization: apiToken,
    },
    url: `${apiEndpoint}/.../${param}?api-version=1.0`, // insert your API
  };

  try {
    const { data } = await axios(config);
    console.log("get monitor data");
    return data;
  } catch (error) {
    console.log(error);
    return false;
  }
};
```
