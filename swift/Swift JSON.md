# Swift JSON #

## Url ##
`var url = NSURL(string: "")`

## Data ##
`var data = NSData(content: url, optents: NSDataReadingOptions.DataReadingUncached, error:nil)`

* error 例外處理內容

## Json ##
`var json: AnyObject = NSJSONSerialization.JSONObjectWithData(data!, options:NSJSONReadingOptions.AllowFragments, error: nil)`

* error 例外處理內容