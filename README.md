# SharePoint Framework Nano Server Docker image

Nano Server Docker image for running [SharePoint Framework](https://github.com/SharePoint/sp-dev-docs).

## Building image

 - Download dockerfile from rep.
 - Execute the following command: 
```cmd
cd [dockerfile location]
docker build -t nanos-o365-spfx .
```

## Usage

- in **Docker Settings > Shared Drives** verify that the drive where you create your projects is shared
- Create a folder for your SharePoint Framework project
- In other shells on Windows (assumes that your project is at `C:\projects\spfx-helloworld`)
```cmd
cd C:\projects\spfx-helloworld
docker run -it -v "%cd%":"C:/cwd" -w="C:/cwd" -p 5432:5432 -p 4321:4321 -p 35729:35729 nanos-o365-spfx
```

After the container started you can work with it the same way you would work with SharePoint Framework installed on your host. To create a new SharePoint Framework project in the container command line execute:

```cmd
yo @microsoft/sharepoint
```

To open the SharePoint workbench navigate in the browser to **https://localhost:5432/workbench**.

All files scaffolded by the generator will be stored in your project directory on your host from where you can commit them to source control.

To close the container in the container command line run:

```cmd
exit
```

## Available tags (TODO)
## Known issues (TODO)

### Unable to write files to disk

When running `yo @microsoft/sharepoint` you get an error that the container is unable to write files to the disk. In most cases this is caused by the drive not being shared in Docker. Go to Docker > Settings > Sharing to enable sharing the drive where your project is located.

## Limitations (TODO)
