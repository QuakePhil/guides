# General Deployment/Network/Connection Issues

## Debugging

![try restarting](https://media.giphy.com/media/F7yLXA5fJ5sLC/giphy.gif)

If an application "is not working," i.e. no data appears to be loading on the frontend because it cannot connect to the
backend, try the following, in order:

- Check to see if the backend application is responding by seeing if its `docs` are available via an http request.
You can put this URL into a browser, or hit it with cURL
`curl http://internal-LB-HFA-US-E-1-T-INT-VPC-HUB-API-2080413110.us-east-1.elb.amazonaws.com/statements/v1/docs`.
- If the backend application is responding, make sure the frontend is configured to access the relevant endpoint
correctly. If the backend application is not responding, try re-running the last deployment for the application in the
appropriate environment on Bamboo (https://bamboo.sesac.com/deploy/viewAllDeploymentProjects.action).
- If after running the deployment, waiting a few minutes for things to reconnect, and it's "still not working," try
inspecting the logs for errors or exceptions that could indicate what is wrong.
- If this still doesn't resolve the issue, try contacting IT to see if there are larger company-wide issues.
