## PM2 Configuration
1. Created config.json file (optix-data-server → pm2 → ecosystem.config.js)

### ecosystem.config.js
```
module.export = {
  "apps" : [
     {
        "name"          : "optix-data-server",
        "script"        : "./build/index.js",
        "instances"     : "max",
        "watch"         : "true",
        "exec_mode"     : "cluster"
     }
  ]
};
```

2. Executed below command in `~/optix-data-server` directory.
```
pm2 start pm2/ecosystem.config.js
```

3. In `ecosystem.config.js` execution mode is set as cluster and instance value as max .

Because of below 2 attributes 

   - `max` means that PM2 will auto detect the number of available CPUs and run as many processes as possible.

   - Set the `exec_mode` to `cluster` so that PM2 know you want to load balance between each instance i.e PM2 will use 2 CPUs (optix-data-server-dev-01 ec2 instance has 2 CPUs) to serve application with the same shared port.

### this command will save the process list	
```
pm2 save 
```