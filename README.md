# sumo-dm-template

To apply, clone this repo locally and cd into the top-level folder. Then, use the Yext CLI to spin up an empty account to which we can apply these templates.

```bash
yext accounts create -u development
```

Note the returned id, and call `yext init -u development`, choose `Create new credential`, and paste in the id where prompted.

Then run
```bash
cd resources
yext resource apply . --on-missing-dependencies ADD
```
note that you *cannot* just skip the cd and run apply on `./resources`, you currently have to cd in for it to recognize the
dependency json.

Once this is done, you can sign into the test account and you should see some predefined entities for you
to work with. When you are ready to run the config on this account, call
```bash
yext dm run --cacId base-dm-config
```
After a few moments, you should have a fully functional directory tree.
