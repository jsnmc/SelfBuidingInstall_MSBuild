# SelfBuidingInstall_MSBuild
Example of simple C# and web application projects that utilize an environment variable to control project output.


This is useful because in large projects, you don't have to have a post build step that collects the components and packages things up.   It is also useful for cases where during development you have to manually copy your components into the install.  With this approach, you can overwrite your installation components with your freshly built components.


Simply modify your projects with the following:

<PropertyGroup>
	<MY_OUTPUT Condition=" '$(MY_OUTPUT)' == '' ">bin</MY_OUTPUT>
    <FinalOutput>$(MY_OUTPUT)\$(Configuration)</FinalOutput>
</PropertyGroup>

MY_OUTPUT will be the enivironment variable that you set to the root location of the install image.  If it is not set, provide a local default.

In the msbuild files simply change the output path:

<OutputPath>$(FinalOutput)</OutputPath>



So set the environment variable on the command line and launch the build with it set.  You can control this with batch files for toggling different options, or permanently set.

![Alt text](/images/P1.PNG?raw=true "Environment variable")


Setting the environment variable, will now change the binary output for the project:


![Alt text](/images/P2.PNG?raw=true "Environment variable")


The output goes to the correct location:
![Alt text](/images/P5.PNG?raw=true "Environment variable")


Without the environment variable set, the output will take the default:

![Alt text](/images/P2.PNG?raw=true "Environment variable")


![Alt text](/images/P4.PNG?raw=true "Environment variable")








