---
title: "Deploying Gatsby"
---

## Best Practice


Though you can deploy from the same location multiple times it is recommended that you clear your public directory of any `.html` files before each build
e.g. using surge

```bash
rm -rf public/*.html && gatsby build && surge public/
```

because this is going to be executed on every deploy it is suggested that you use a `package.json` script to simplify this process

## Providers

[Surge.sh](http://surge.sh/)

[Forge](https://getforge.com/)

[Netlify](https://www.netlify.com/)

[GitHub-Pages](https://pages.github.com/)

## Debugging

### Don't minify HTML

If you see the following error:

```
Unable to find element with ID ##
```

or alternatively

```
Uncaught Error: Minified React error #32; visit http://facebook.github.io/react/docs/error-decoder.html?invariant=32&args[]=## for the full message or use the non-minified dev environment for full errors and additional helpful warnings.
```

This is a new problem when dealing with static sites built with React.  React uses HTML comments to help identify locations of components that do not render anything.  If you are using a CDN that minifies your HTML, it will eliminate the HTML comments used by react to take control of the page on the client.

## Hosting on Amazon S3 and Cloudfront
If you decide to host your Gatsby site to S3 having Cloudfront as CDN you should edit on the Cloudfront panel the "Origin Domain Name" with the real URL of your S3 bucket: **examplewebsite.com.s3-website-eu-west-1.amazonaws.com** instead of the default one automatically suggested by Amazon **examplewebsite.com.s3.amazonaws.com**. 

This is recommended for rendering correctly the post pages in the subfolders without typing the index.html path as described [here](https://forums.aws.amazon.com/message.jspa?messageID=314454).  
