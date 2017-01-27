node-runner
==================

Run node process in parrallel and merge all console output in one place

### Setup

clone this git repo locally and run `npm install`

### How to run

In Package.json, modify scripts section to meet your need

```
"scripts": {
	"reporting": "cd ../../projects/reporting-static/ && grunt work",
	"payment": "cd ../../projects/payment-static/ && grunt work",
	"start": "concurrent -k \"npm run payment\" \"npm run reporting\""
}
```
you can write new scripts simmilar to 'reporting' and 'payment' scripts which navigate to the root directory where you have the package.json of the project you want to run and then run the task. Task could be 'grunt', 'gulp' or 'npm'.

```
"angular-server": "cd ../../projects/angular-project/ && gulp serve",
```

now reference your scripts in the 'start' script. All the three tasks listed below will now run in parrallel.

```
"start": "concurrent -k \"npm run payment\" \"npm run reporting\" \"npm run angular-server\" " 
```

now run 'npm start' to run the process

documentation on concurrently [concurrently/README](https://github.com/kimmobrunfeldt/concurrently/blob/master/README.md)