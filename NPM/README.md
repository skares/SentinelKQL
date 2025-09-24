Custom Defender Detection Rule to match npm install processes against a Sentinel watchlist with malicious NPM packages

1.) Upload the CSV File to a Watchlist in Sentinel. Ensure Watchlist Name is the same as in the query.

2.) Execute the Query and if nothing shows up i recommend to add one well known package to the watchlist for testing.

3.) Create a custom Detection Rule in Defender and execute it every 3h, 12h, or 24h.
