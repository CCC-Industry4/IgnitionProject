[Back to Main Menu](https://github.com/CCC-Industry4/IgnitionProject/tree/main)
# Smart Home
---

1. Namespace Usage/Session Custom Properties 
    - The Ignition project uses an [MQTT Engine](https://inductiveautomation.com/resources/article/what-is-mqtt) to organize the smart home data. For more information on Ignition's Tag system, visit their official documentation located [here](https://www.docs.inductiveautomation.com/docs/8.1/platform/tags).
    - Ignition does not support client-side tags, so we instead use [Session Custom Properties](https://www.docs.inductiveautomation.com/docs/8.1/ignition-modules/perspective/perspective-sessions/session-properties), located in the bottom right of the image below.

    ![Namespace Area](/images/smarthome/smarthome02.jpg)
    
    - This Namespace is used as the path for writing and reading tags from the central server to the Smart Homes.
    - If you right-click on the namespace property, and click configure binding you can see the python script we use to generate the namespace.

    ![Namespace](/images/smarthome/namespace.jpg)

    - The home and neighborhood properties are also stored client-side, and we use scripts on pages in order to update them to the desired values.
    - The reason we have all these properties stored client-side is so that multiple users can operate the website and manipulate differnet homes simultaneously. Otherwise changing the active home and neighborhood for one user would change it for all users.

    ![Namespace Binding](/images/smarthome/namespacebinding.jpg)
    
    - Here is an example of how we use the namespace property. The LED Color values are found using the namespace as a path, and then reading the values of the corresponding tag on the ignition server.

2. Nagivate to Smart Home page

    ![Nagivate to Smart Home Page](/images/smarthome/smarthome01.jpg)

    - On the right you'll see various Perspective pages we've created for the website. You can navigate to the Smart Home page by either clicking on ViewSmartHome (landscape) on the left or using clicking on /smarthome on the center.

3. Dropdown
    
    - The dropdown for the neighborhood number and the dropdown for the home number is how we update the Custom Session Properties named home and neighboorhood.  

    ![Click Dropdown](/images/smarthome/clickdropdown.jpg)

    - Right-click on one of them and then select Configure Events. This will let you see the python scripting we use to update the values of the Custom Session Properties.

    ![onStartup](/images/smarthome/dropdownstartup.jpg)

    - onStartup runs when the page is loaded. This is to prevent the issue where the page loads and the currently selected home and the dropdown aren't matching. 

    ![onAction](/images/smarthome/dropdownaction.jpg)

    - onAction runs when you select an option on the dropdown. This is how we change which neighboorhood or home we are currently using.

    ![onClick](/images/smarthome/dropdownonclick.jpg)

    - onClick runs whenever a user clicks on the dropdown. This runs a script to refresh the options so we can see if any homes have been disconnected or added to the network.
    
    ![Configure Binding](/images//smarthome/dropdownconfigbinding.jpg)

    - If you wish to see the python script, go to the Perspective Property Editor tab and right click on options. Then click on configure binding to see the script that controls how the options refresh.

    ![Dropdown Script](/images/smarthome/dropdownscript.jpg)

4. Additional Info

    - There is an onClick script for the entire page that writes to the namespace tags. This is because we use the tag system to manage writing and reading from the server to the smart homes. A limitation is that you can normally only write/read to one object at a time. Tags don't play nice with custom session properties as far as I can recall (may be worth researching) so we use a hacky method that just swaps the Ignition Namespace tag to whatever client is trying to write to the smart home whenever they interact with the webpage. 

---