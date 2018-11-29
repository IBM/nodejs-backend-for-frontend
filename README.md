[![](https://img.shields.io/badge/IBM%20Cloud-powered-blue.svg)](https://bluemix.net)
![Platform](https://img.shields.io/badge/platform-nodejs-lightgrey.svg?style=flat)

# Create and deploy a Node.js Backend For Frontend (BFF) using Express

> We have similar patterns available for [Swift](https://github.com/IBM/swift-backend-for-frontend), [Java Spring](https://github.com/IBM/spring-backend-for-frontend), and [Java Liberty](https://github.com/IBM/java-liberty-backend-for-frontend) as well!

The Backend for Frontend pattern, commonly known as BFFs, helps you focus on exposing business data and services in a form that matches the user interaction requirements. For instance, to optimize a user journey to your cloud solution, it may require a different user journey for the mobile application but a richer, more detailed journey for the Web application. With IBM Cloud, you can build a BFF by using polyglot programming approach to define the BFF- using Node.js, Swift, or Java. The BFF service exposes a RESTful API matching a [Swagger](http://swagger.io) definition.

![](doc/source/images/architecture.png)

## Requirements

### Local Development Tools Setup (optional)

- Install the latest [NodeJS](https://nodejs.org/en/download/) 6+ LTS version.

### IBM Cloud development tools setup (optional)

1. Install [IBM Cloud Developer Tools](https://console.bluemix.net/docs/cli/idt/setting_up_idt.html#add-cli) on your machine
2. Install the plugin with: `ibmcloud plugin install dev -r IBM Cloud`

### IBM Cloud DevOps setup (optional)

[![Create Toolchain](https://console.ng.bluemix.net/devops/graphics/create_toolchain_button.png)](https://console.ng.bluemix.net/devops/setup/deploy/)

[IBM Cloud DevOps](https://www.ibm.com/cloud-computing/bluemix/devops) services provides toolchains as a set of tool integrations that support development, deployment, and operations tasks inside IBM Cloud. The "Create Toolchain" button creates a DevOps toolchain and acts as a single-click deploy to IBM Cloud including provisioning all required services.

***Note** you must publish your project to [Github](https://github.com/) for this to work.

## Configuration

The project contains IBM Cloud specific files that are used to deploy the application as part of an IBM Cloud DevOps flow. The `.bluemix` directory contains files used to define the IBM Cloud toolchain and pipeline for your application. The `manifest.yml` file specifies the name of your application in IBM Cloud, the timeout value during deployment, and which services to bind to.

Service credentials are taken from the VCAP_SERVICES environment variable if running IBM Cloud Cloud Foundry, from individual environment variables per service if running on IBM Cloud Container Service (see ./server/config/mappings.json), or from a config file if running locally, named`./server/config/localdev-config.js`.

## Run

### Using IBM Cloud development CLI

The IBM Cloud development plugin makes it easy to compile and run your application if you do not have all of the tools installed on your computer yet. Your application will be compiled with Docker containers. To compile and run your app, run:

```bash
ibmcloud dev build
ibmcloud dev run
```

### Using your local development environment

#### Endpoints

Your application is running at: `http://localhost:3000/` in your browser.

- Your [Swagger UI](http://swagger.io/swagger-ui/) is running on: `/explorer`
- Your Swagger definition is running on: `/swagger/api`
- Health endpoint: `/appmetrics-dash`

#### Session Store

You may see this warning when running `bx dev run`:
```
Warning: connect.session() MemoryStore is not
designed for a production environment, as it will leak
memory, and will not scale past a single process.
```
When deploying to production, it is best practice to configure sessions to be stored in an external persistence service.

## Troubleshooting

### Using IBM Cloud development CLI

To build and debug your app, run:

```bash
ibmcloud dev build --debug
ibmcloud dev debug
```

## License

[Apache 2.0](LICENSE)
