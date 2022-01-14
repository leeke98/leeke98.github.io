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
  <img src="assets/env_setting.png">

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

You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

Jekyll requires blog post files to be named according to the following format:

`YEAR-MONTH-DAY-title.MARKUP`

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]: https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
