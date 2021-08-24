## ServerlessPrinting

This repository contains all the documentation for the ServerlessPrinting project.
This project should eventually replace all of the ReportDaemon functionality.

These are the different sub-projects:

### [CrystalReportsApi](crystalreportsapi.md)

This is the central piece. 
The API that actually generates the pdf and puts it in blob storage. 
This is also the entry point for starting a print flow 
from the viewpoint of this ServerlessPrinting solution.

This part is built using ASP.NET WebAPI 2 running on .NET Framework, as that's
necessary for the Crystal Reports Components (they only run on .NET Framework at the moment).
It is packaged up as a docker image (built with windows2019ltsc as base) for ease of deployment.

The dev version is at the moment deployed as an Azure Container Instance and is 
available [here](http://serverlessprintingdev.westeurope.azurecontainer.io/).

### ServerlessPrintingClient

This is the part that runs on the client, listens for "PrintCommands" and executes them.
This should replicate the functionality of ReportDaemon (printing documents, mailing them,
opening them for previewing). 

This is now implemented using Winforms on .NET Framework, <s>packaged up as a click-once
application for ease of deployment</s>.

(I have tried building it for .NET 5 but the controls that are used now are not yet 
working in that environment.)

The dev version is at the moment deployed as a zip file containing a release build 
on the Azure Storage account, available [here](https://serverlessprintingdev.z6.web.core.windows.net/ServerlessPrintingClient.zip).

### [FunctionApp](functionapp.md)

This is the piece that glues everything together. 

It has a function that triggers on blob uploads (from the CrystalReportsApi) and that
sends a printcommand to the client.
It also exposes a couple of endpoints for the client to connect to and download and delete pdf's.

The dev version is at the moment deployed as a FunctionApp on Azure and is available
[here](https://serverlessprintingdev.azurewebsites.net/).

### [CrystalReportsRuntime](crystalreportsruntime.md)

This is a docker build project for building a base image which contains the
Crystal Reports Runtime Components and the necessary fonts.
