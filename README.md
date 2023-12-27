This is an import script for getting R-Squared transactions.

This script uses the [`rsquared-js-ws`](https://github.com/R-Squared-Project/R-Squaredjs-ws) library to make a connection to the R-Squared blockchain, fetches all transactions for a given user, and converts it to a CSV file.

# Usage

This script requires Node to run; install Node locally and run:

```
yarn
yarn start myUsername [debug] [no_grouping] [op_type_filter]
```

Replace `myUsername` with the R-Squared user you wish to make a report for. Since R-Squared data is completely open, there are no login credentials needed to get a full transaction report on any user.

The debug, no_grouping and op_type_filter parameters are optional.
`debug = true|false, default = false`
`no_grouping = true|false, default = false`
`op_type_filter = transfer, fill_order, etc, default=none`

Running the script will create a `{username}-rqrx-transactions.csv` file in the `output` folder of the project.

## Automating multiple accounts

If you have several accounts you can rename `run_accounts_example.sh` and input your desired accounts there as shown. Then run it using `. ./run_accounts.sh`. This will fetch data for all accounts and generate a file called `all-merged.csv` in the root folder.

# Caveats

An important limitation right now is that the API node used needs to be configured to store all operation history. That means setting the `max-ops-per-account` parameter in config.ini to a high value, I've used `max-ops-per-account = 200000` successfully for my own accounts. A replay of the blockchain is necessary after changing this parameter.
