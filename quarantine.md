If you download your favorite CLI tool from GitHub and try to run it, you will find that macOS Gatekeeper gets in your way. You have to go to Settings -> Privacy -> and click "Allow anyway" to let the particular file be executed. However, no surprise here, you need Administrator permissions to click that button. Luckily, this system is not as onerous as you might think. macOS is not peering into this binary and deciding it is unfit for execution. It's actually looking at a simple filesystem flag called the quarantine flag. That quarantine flag is set upon download by your browser and, you guessed it, you can't remove the flag without Administrator permissions.

However, you can download the file with curl instead. curl does not set any quarantine flag upon download. Then you are free to use all the amazing tools found in GitHub.

You can download files with curl via `curl -L -O my-url-here`


