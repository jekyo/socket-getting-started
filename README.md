# Tutorial: Deploying a basic Socket app on Jekyo

Demo app [here](https://socket-demo.jekyo.app/)

### Prerequisites

Make sure you have [NodeJS](https://nodejs.org/en/download/), [npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) and [git](https://github.com/git-guides/install-git) installed.

If it's your first time using **Jekyo**, you can **install** it by running the following command in your terminal:

`npm install -g jekyo`

### Sign in to Jekyo

You can sign in to Jekyo by running `jekyo user:signin`

```
➜  ~ jekyo user:signin 
Your email?: **************
Your password?: **********
You have successfully signed in!
```
If you don't have a Jekyo account, you can create one in the terminal by running `jekyo user:signup`. 

## 1. Create a basic Socket app

You can start your Socket project by using `jekyo create`

Using the **arrows** on your keyboard, select **socket** and press **enter**.  
```
? Select template
  None Creates only the application
  expressjs A basic app skeleton using [Express](https://expressjs.com/)     
  nuxt-js A boilerplate SSR application using [Nuxt.js](https://nuxtjs.org/) 
❯ socket A basic starter app using [Socket](https://placeholder.dev/)
```
When prompted, enter the desired name for your Socket app. 

`Application name?: socket-tutorial`

This will create a basic Socket app in the current directory by cloning this [Socket starter app](https://github.com/jekyo/socket-getting-started) repository.

```
Cloning source code... OK
Application created!
```

### Deploy the Socket app on Jekyo

To deploy the app, first navigate to the newly created directory:

`cd socket-tutorial`

Now you can deploy this app to Jekyo by running: 

`jekyo deploy`

After a while, you should see something like this:

```
➜  Fetching source code ... OK
➜  Building application, this might take a while ... OK
➜  Publishing application, this might take a while  ... OK
➜  Deploying application ... OK        
➜  Waiting for application to start ... OK
➜  Visit your app on: https://socket-tutorial.jekyo.app ... OK
```

You can now browse to your Socket app on https://socket-tutorial.jekyo.app (replace 'socket-tutorial' with your app name)

## 2. Deploying an existing Socket app

Navigate to your local Socket app directory

`cd my-socket-app`

Initialize a git repository if you haven't already done so by running `git init`. 

### Edit package.json

Make sure **scripts** in your _package.json_ file includes a start line and pass the $HOST variable:

```
"scripts":{
    "start": "node index.js --host $HOST"
}
```

### Edit index.js port

In your **index.js** file, replace port with _process.env.PORT_, which specifies Jekyo's preferred port.

```
server.listen(process.env.PORT, () => {
  console.log('listening on *:process.env.PORT');
});
```

### Create an empty Jekyo app:

`jekyo create` 

Select 'none' using the **arrows** on your keyboard and press **enter**. This will create an app using your current directory. 

```
? Select template (Use arrow keys)
❯ None Creates an application from your current directory
```

Name your app: 

`Application name?: my-socket-app`

Run `jekyo link` to link your local app to the remote Jekyo app. Select 'my-socket-app' using the **arrows** on your keyboard and press **enter**.

```
? Select application (Use arrow keys)
❯ my-socket-app
```
### Now you can deploy this app to Jekyo by running: 

`jekyo deploy`

After a while, you should see something like this:

```
➜  Fetching source code ... OK
➜  Building application, this might take a while ... OK
➜  Publishing application, this might take a while  ... OK
➜  Deploying application ... OK        
➜  Waiting for application to start ... OK
➜  Visit your app on: https://my-socket-app.jekyo.app ... OK
```

You can now browse to your Socket app on https://my-socket-app.jekyo.app (replace 'my-socket-app' with your app name)

## Pushing local changes to Jekyo 

Add the newly modified file(s) to the git index by using [git add](https://www.atlassian.com/git/tutorials/saving-changes)

`git add filename`

Create a [git commit](https://github.com/git-guides/git-commit)

`git commit -m "your commit message"`

Now, simply deploy your app again:

`jekyo deploy`

You will see your changes on your live app after a short while. 