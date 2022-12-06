# Directory Manager Account Template

To apply, clone this repo locally and cd into the top-level folder. Then, use the Yext CLI to spin up an empty account to which we can apply these templates.

```bash
yext accounts create -u development
```

Note the returned id, and call `yext init -u development`, choose `Create new credential`, and paste in the id where prompted.

The directory config can be found at `resources/default/pages/directory-manager/base-dm-config.json`. Feel free to modify it if you have certain properties you
want to test.

When you are ready to apply your data, run
```bash
cd resources
yext resources apply . --on-missing-dependencies ADD
```
note that you *cannot* just skip the cd and run apply on `./resources`, you currently have to cd in for it to recognize the
dependency json.

Once this is done, you can sign into the test account and you should see some predefined entities for you
to work with. Feel free to modify these as needed (you can also modify their json files before applying, but I find it
typically easier to edit entities via the UI).

To test the config locally, go through the normal flow with the grpc UI.

If you want to run against the dev directory manager rather
than locally, you can do
```bash
yext dm run --cacId base-dm-config
```
After a few moments, you should have a fully functional directory tree.

## Running in other environments

Since feature ids and the like are typically kept constant across environments, it should be possible to apply this account template in any env.
When running create/init, simply update the `-u` field from `development` to `qa/sandbox`, or leave it blank for production.
