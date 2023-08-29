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

Upload ~/jquery-application-toastr/sharepoint/solution/toastr.sppkg to Sharepoint Apps, enable for all sites.
### Sharepoint: Manually create the list

1. Navigate to the Site Contents page and choose **New** > **List**
2. Name the list _**Toast**_ and click **Create**
3. Add and configure the columns as listed below:

Column | Type | Required | Details
--- | --- | --- | ---
Title | Text | Yes |
Message | Text | Yes |
Severity | Choice | Yes | Info, Warning, Error, Success
StartDate | DateTime | Yes | Date and Time, Default =Today
EndDate | DateTime | Yes | Date and Time, Default =Today+7
Frequency | Choice | Yes | Once, Once Per Day, Always
Enabled | Yes/No | | Default = Yes

Add an item to the list. Do not use the same EndDate as the StartDate or it will not show.

### SPFx - Add Custom List to Sharepoint

1. `cd ~/jquery-application-toastr`
2. `nvm install 16`
3. `nvm use 16`
4. `npm install -g @pnp/cli-microsoft365`
5. `m365 login`
Your web browser will open to: https://microsoft.com/devicelogin enter the code provided to login and follow prompts. 
```
~/jquery-application-toastr$ m365 login
"To sign in, use a web browser to open the page https://microsoft.com/devicelogin and enter the code CHHJUMAPW to authenticate."
{
  connectedAs: 'username@sptenant.onmicrosoft.com',
  authType: 'DeviceCode',
  appId: '41354c7f-bd7e-475c-86db-fdb8c937548e',
  appTenant: 'common',
  cloudType: 'Public'
}
```
You are now connected to your Sharepoint site.

6. Update the following command. Replacing --webUrl with the site you want to show Toast notifications on. Update --clientSideComponentId with your application Id. This is located in
~/jquery-application-toastr/src/extensions/spfxToastr/SpfxToastrApplicationCustomizer.manifest.json - "id". Since we are working off a specific example, you will not need to update it since it will be the same as the current value.

Then run it.

```
m365 spo customaction add --webUrl https://SPTENANT.sharepoint.com/sites/SampleSite --title "Toastr Notifications" --name "jquery-application-toastr" --location "ClientSideExtension.ApplicationCustomizer" --clientSideComponentId a861c815-e425-416d-9520-04bcdf557e27 --clientSideComponentProperties ''
```

After the command completes, refresh the site. You should see the Toast Notification. 

If you want to create a new build, you will need to revert back to nodejs 8.
```nvm use 8```
