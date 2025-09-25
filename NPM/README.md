# Custom Defender Detection Rule to match npm install processes against a Sentinel watchlist with malicious NPM packages

## Setup Steps
1. Upload the CSV File to a Watchlist in Sentinel. Update the watchlist before or after upload to have an up2date list. Ensure that the Watchlist Name is the same as in the query.

2. Execute the Query and if nothing shows up i recommend to add one well known package to the watchlist for testing.

3. Create a custom Detection Rule in Defender and execute it every 3h, 12h, or 24h.


## Help
regex:
extract_all(@"((?:@[^@\s/]+/)?[^@\s]+)@([^\s]+)"

(?:@[^@\s/]+/)? == the @ symbol, followed by one or more characters that are not @, whitespace, or /, then a /. --> npm package or @xyz/package

?[^@\s]+)@([^\s]+) --> Matches one or more characters that are not whitespace. This is everything after the @ symbol.
Examples: 
mypackage@1.0.0
→ Group1 = mypackage, Group2 = 1.0.0
@org/mypackage@2.3.4
→ Group1 = @org/mypackage, Group2 = 2.3.4

dynamic([1,2])
This tells extract_all to return both group 1 and group 2 for each match.
So the result will be an array of arrays, like:
[
  ["mypackage", "1.0.0"],
  ["@org/mypackage", "2.3.4"]
]