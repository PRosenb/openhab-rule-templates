![alert-svgrepo-com|50x50](upload://kQ5n4L15WGDj3n88IxswPMs4yem.svg)

This template supervises not ignored Things. When a Thing is offline, it changes the item `Things online item` to `off` and creates a new item under `Parent item` with the label set to the label of the Thing that is offline. Then it switches that item to `off`.
When the Thing is online again, the created item is not deleted but switched to `on`. That way offline/online history is kept and you can analyse, when Things were offline to find potential problems.

To setup this template, follow these steps.

Prepare the item:
* Click on `Settings` -> `Model`
* On the right, click on `Add Equipment`
* Name: `OnlineThings`, Label: `Online Things`
* Click `Create`
* Click `Add Metadata` -> `State Description`
* Toggle on `Read only` and `Save` (top right)
* Click on `Online Things` to open it
* Click `Edit` on top right
* Set `Members Base Type` to `Switch`
* Click `Save` (top right)

Install the template:
* Click on `Settings` and then on `Automation`
* Scroll to ` Rule Templates` and click on `Show xx more`
* Click the `ADD` button on `Offline Things Display`
* Click the large `ADD` button on the pop up

Setup the rule:
* Go to `Rules` and create a rule from `Offline Things display`.
* Select the above item `Online Things` as `Parent item`,  `Ignored Things item` and `Things online item`.
* Force a Thing to be offline by e.g. removing power from it
* Check the item `Online Things`, it should go to `off` and an item named after the offline Thing should be created inside.

Ignore a Thing:
* Go to `Settings` -> `Things`
* In the list, on the Thing you want to ignore, click the square `Copy UID`
* Click on `Settings` -> `Model`
* Click on `Online Things`
* On the right, click on `Online Things` to open it
* Click `Edit` on top right
* Paste into `Add tag` and press `enter`
* Click `Save` (top right)

Show it on a page:
* Click on `Settings` -> `Pages`
* Click on `Overview` (or an other page you want)
* If you don't have rows/columns, click `Add Row` and on the row `Add Column`
* Click on it and choose `List card`
* Click on the `+` and choose `Label List Item`
* Click on it and `Edit YAML`
* Paste the code `YAML for Label List Item` below into it
* Click `Done` and `Save` (top right)

Note:
Then you use a `Group` as `Things online item`, the state `on` and `off` is only visible if at least one item was created within the group.
Inputs, corrections and suggestions are very welcome.

Detection of offline Things is based on the template [Thing Status Reporting](https://community.openhab.org/t/thing-status-reporting-4-0-0-0-4-1-0-0/143180). My first approach was to use it to implement this template. But it turned out more complicated than implementing that part myself.
