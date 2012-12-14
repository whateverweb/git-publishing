# Publishing your website with WEW

Publishing with WEW can be used for tasks like quick prototyping, real device testing and client testing. It can even be used for running your site in production, in an environment where we strive to do as much of the optimizations as possible without you having to worry about it. Some tasks like image processing, preprocessing and javascript/CSS compression are performed once when you publish your site. Other optimizations, like serving compressed resources, cache friendly headers and resources are handled per request by our delivery servers.

Hosting on WEW is based on *git*. When enabling this option in the WEW control panel you are given your own *git* repository. This actually means that you also get full-fledged source control management for your site when publishing with WEW.

##### Features
* Image optimization
	* Published images will be optimized for web (removing EXIF data, checking or/and adjusting compression and quality levels)
* JavaScript optimization
	* JavaScript will be compressed (configurable)
* CSS
	* SASS-support: both SASS and SCSS files will be preprocessed to CSS when published. Supports Compass extensions
	* CSS files are served using the WEW SSMQ engine, which will strip away styles irrelevant for requesting device, provide extended (server side) media query capabilities and inline import statements
* Markup
	* Published HTML will be optimized (configurable)

### Setting up your GIT repository

Prerequisites:
 * a *git* client
 * an *SSH* client (only if you don't have a public key)

 Install a *git* client from [http://git-scm.com/download/](http://git-scm.com/download/) -- or use any other client you might prefer.
 The SSH client is normally installed per default on Mac OS X and Linux distributions, on Windows [PuTTY / puttygen](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) is a classic.

In order to secure your repository we need your SSH *public* key. This is normally located in the .ssh folder of your home directory. If you don't have one, check out the ssh-keygen (OSX/Linux) or puttygen (Windows) tool. When you have your key, paste it into the WEW control panel. The repository will be created and available within a few minutes.

The (git) URL for your repository will be displayed in the control panel. It is typically something like: *git@scm.wew.io:aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee.git*

### Using GIT to publish your website

NOTE: The following is only a crash-course to *git*. Lots of *git* functionality and details are omitted. We highly encourage you to head over to the [official Git documentation](http://git-scm.com/doc) if you want to learn some more about this great source control management system.

1. Initialize a folder

		git clone git@scm.wew.io:00000000000000.git [a friendly name]

	This will create a subfolder named after your application id. (The friendly name is optional, without it your new subfolder will be named after your application id -- not everyone's cup of tea...)

2. Create and add some content

	In your new subfolder, go ahead and create some files, an 'index.html', some CSS etc might be a good start.

	For each file you create that is part of your deployment, do:

		git add <filename>

	Or, if all your files (and subfolders) are to be added, do:
	
		git add -a

3. Commit your changes

	When you have changed something in your file(s) you should commit your changes. This is a standard 'git' operation, local to your computer.

		git commit <file> -m "A description of your change"

4. Publish

	Perform a standard 'git' push operation to publish your site. If it is your first push, you normally have to do:

		git push origin master

	After your first push a simple 'git push' from your local folder will probably be sufficient.

5. Test

	Whenever you 'push' your changes to the WEW repository your site will be preprocessed, optimized and finally published to your configured hostname. Please note that your deployment is placed in a queue, so it might take a few minutes before your changes are live.

	Test your site by pointing any browser on any device towards your URL.