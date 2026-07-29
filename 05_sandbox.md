[Back to Main Menu](https://github.com/CCC-Industry4/IgnitionProject/tree/main)

# Sandbox

---

1. Overview and Namespace

    ![Overview](/images/sandbox/sandbox0.jpg)

    - This is the sandbox page. It is used to setup conditional inputs to trigger outputs.

    ![1](/images/sandbox/sandbox1.jpg)

    - At the top of the page you can see the namespace. It shows you the path of the currently selected house that you can create basic rules for.

2. Inputs, Conditions, Setpoints, and Outputs

    ![2](/images/sandbox/sandbox2.jpg)

    - Inputs form the beginning of a sandbox rule. They are a device on the smart home that you can then apply logic in order to trigger an output.
        - Examples are pushbuttons, motion detection, or reading a numerical value from temperature or humidity.
    - Conditions are used to define the logic the rule uses. The most basic logic is to check if an input is on or off.
    - For binary inputs like pushbuttons, you can check if something is off/on, or set it to as a toggle for a rule. For non-binary inputs that return values like 
    - Setpoints are used for a subsection of inputs. Certain inputs (like temperature) are more complex and return a numerical value, rather than a simple on/off.
    - Outputs are components of the smart home that are turned on/off when the logic is true.
    - Each of the 4 drop downs have their own tags created and placed in the AutomationLogic folder, all bound to their respective value property. This is done because there is also a tag in the AutomationLogic folder called LiveSensorValue, which controls almost all of the sandbox functions, and it reads the value of each of the 4 drop downs to determine what to do, and this value is retrieved from the 4 tags.

3. Saving and Running Rules

    ![3](/images/sandbox/sandbox3.jpg)

    - Starting and stopping the sandbox is controlled by the SYSTEM ON and SYSTEM OFF buttons.
    - You can save a rule with the logic you've input into the dropdowns by hitting the Save Rule button. You can also delete a rule by selecting it in the table below and clicking Delete Rule.

4. Rule Table   

    ![4](/images/sandbox/sandbox4.jpg)

    - This table holds all the saved rules for the sandbox.
    - All rules in the table are always active. For example, if there is a rule in the table for a button to turn on the yellow led, and another rule for that same button to open the door, when the button is pressed, both commands will be executed.


---
