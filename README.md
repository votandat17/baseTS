*/ This is my base enviroment. I create it to use later /*
to get full if this feature we need download with npm
all commands are here:
* npm install typescript //this command will download the lastest typescript version


* npm init -y  // this command will create a file package.json with default 
-   Open file package.json and add this into script:
    {   
        ...
        "scripts": {
            "build": "tsc",
            "start": "node dist/index.js",
            "dev": "tsc --watch"
        },
        ...
    }

*  tsc --init // this command will create a file tsconfig.json

-   you should change the file like this: 
        {
            "compilerOptions": {
                "target": "ES2022",  
                "module": "commonjs", 
                "strict": true, 
                "esModuleInterop": true,  
                "outDir": "./dist", 
                "rootDir": "./src", 
                "skipLibCheck": true 
            },
            "include": ["src/**/*"],
            "exclude": ["node_modules"]
        }

*   if you want to compile your code without javascript so download ts-node  with : //npm install ts-node typescript --save-dev
-   if you downloaded ts-node so add some feature: 
        {
            ...
            "main": "src/index.ts"
            "scripts": {
                "dev": "ts-node src/index.ts",
                "build": "tsc",
                "start:build": "node dist/index.js"
            },
            ...
            "devDependencies": {
                "ts-node": "^10.9.2",
                "typescript": "^5.5.4"
            }
        }
* add nodemon if you want a tool that helps track changes in source code and automatically restart Nodejs applications. 
 // npm install -D nodemon

-   update package.json file with:
    {
        ...
        "script": {
            "dev": "nodemon --watch src --exec ts-node src/index.ts",
            ...
        },
        ...
        "devDependencies": {
            "nodemon": "^3.1.4",
            ...
        }
    }

*   Now you can run your code with command: npm run dev 
*   Create a file with name nodemon.json and inside the file we should add: 
    {
        "watch": ["src"],
        "ext": "ts",
        "exec": "ts-node src/index.ts"
    }

    * watch: Specify the folder to monitor for changes.
    * ext: Format the files to be monitored.
    * exec: command to execute when there is a change. nodemon will run ts-node src/index.ts when there are changes.
