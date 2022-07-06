# node-js-first

## Task:
To create a azure container registry and create a github repository and then create github action pipeline which when pushed builds a docker image from main branch on every merge/commit to main, and then publishes this latest docker image to azure container registry with commit tag.

## Steps:

### Application:
- To accomplish the task I have used a simple node.js application.
- Created a dockerfile for the following application.
- Saved the application in a folder named `node-js-first` .

### Creating ACR:
- Signed into azure portal and serached for conatiner registry in the marketplace.
- Created a container registry.

### Creating Repo On Github:
- Logged into my github account and created a new repository `node-js-first`.

### Pushing my application on Github Repo:
- Opened my application folder on VS Code on my machine and opened terminal in VS Code.
- I built my image using command `docker build -t  myazure69.azurecr.io/node-js-first:firsttry . `
- After the image was built successfully used following commands to push my appliaction on github.
```
git init
git remote add origin https://github.com/Shaw-00/node-js-first.git
git add .
git commit -m "Init"
git push
```
- Logged into docker by `docker login myazure69.azurecr.io` .
- Pushed the image using the command `docker push myazure69.azurecr.io/node-js-first:firsttry` .
- After the push was succesfull created a web app for container keeping the resource group name same as container registry.
- In the tab docker changed the image source to azure container registry and selected the image and tag.
- After that clicked on `review and create` and the web app was created.
- Once web app was created went to the tab `Deployment Center`
- In `Settings` tab turned on continuous deployment and in the `source` tab changed the source to github action
- Github signin dialogue box appeared logged in the gihhtub account.
- Selected `Organization`, `Repository` and `branch` name in the `Github Actions` tab.
- Just previewed the file and saved the file.
- Tapped on build logs to see the building process.
- After a while the building was successfull.
- In the github repository the new pipeline was created under the directory `.github\workflow\main_shaw69.yml`
