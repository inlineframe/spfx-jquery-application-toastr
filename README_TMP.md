# SPFx Compatibility List
https://learn.microsoft.com/en-us/sharepoint/dev/spfx/compatibility

# SPFx Steps
https://github.com/pnp/sp-dev-fx-extensions/tree/main/samples/jquery-application-toastr

1. `mkdir git`
2. `cd git`
3. `git clone https://github.com/pnp/sp-dev-fx-extensions.git`
4. `cd ~/`
5. `cp -aR ~/git/sp-dev-fx-extensions/samples/jquery-application-toastr ~/`
6. `sudo curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash`
7. `cd ~/jquery-application-toastr`
8. `nvm install 8`
9. `nvm use 8`
10. `npm install npm@4 -g` 
11. Confirm you are using Nodejs version 8 and NPM version 4`node -v ; npm -v`
12. `npm install`
13. `gulp build`
14. `gulp bundle --ship`
15. `gulp package-solution --ship`

