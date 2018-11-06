
Versions \| [v1.0 (td-agent3)](/v1.0/articles/formatter_csv) \|
***v0.12* (td-agent2) **
------------------------------------------------------------------------

csv Formatter Plugin
====================

The `csv` formatter plugin output an event as CSV.

``` {.CodeRay}
"value1"[delimiter]"value2"[delimiter]"value3"\n
```


### Table of Contents

[Parameters](#parameters)

-   [fields (Array of String, Required. defaults to
    "\\t"(TAB))](#fields-(array-of-string,-required.-defaults-to-%E2%80%9C%5Ct%E2%80%9D(tab)))
-   [delimiter (String, Optional. defaults to
    ",")](#delimiter-(string,-optional.-defaults-to-%E2%80%9C,%E2%80%9D))
-   [force\_quotes (Boolean, Optional, defaults to
    true)](#force_quotes-(boolean,-optional,-defaults-to-true))
-   [add\_newline (Boolean, Optional, defaults to
    true)](#add_newline-(boolean,-optional,-defaults-to-true))
-   [include\_time\_key (Boolean, Optional, defaults to
    false)](#include_time_key-(boolean,-optional,-defaults-to-false))
-   [time\_key (String, Optional, defaults to
    "time")](#time_key-(string,-optional,-defaults-to-%E2%80%9Ctime%E2%80%9D))
-   [time\_format (String. Optional)](#time_format-(string.-optional))
-   [include\_tag\_key (Boolean. Optional, defaults to
    false)](#include_tag_key-(boolean.-optional,-defaults-to-false))
-   [tag\_key (String, Optional, defaults to
    "tag")](#tag_key-(string,-optional,-defaults-to-%E2%80%9Ctag%E2%80%9D))
-   [localtime (Boolean. Optional, defaults to
    true)](#localtime-(boolean.-optional,-defaults-to-true))
-   [timezone (String. Optional)](#timezone-(string.-optional))

[Example](#example)
Parameters
----------

### fields (Array of String, Required. defaults to "\\t"(TAB))

Specify output fields

### delimiter (String, Optional. defaults to ",")

Delimiter for values.

### force\_quotes (Boolean, Optional, defaults to true)

If false, value won't be framed by quotes.

### add\_newline (Boolean, Optional, defaults to true)

Add `\n` to the result.

### include\_time\_key (Boolean, Optional, defaults to false)

If true, the time field (as specified by the `time_key` parameter) is
kept in the record.

### time\_key (String, Optional, defaults to "time")

The field name for the time key.

### time\_format (String. Optional)

By default, the output format is iso8601 (e.g. "2008-02-01T21:41:49").
One can specify their own format with this parameter.

### include\_tag\_key (Boolean. Optional, defaults to false)

If true, the tag field (as specified by the `tag_key` parameter) is kept
in the record.

### tag\_key (String, Optional, defaults to "tag")

The field name for the tag key.

### localtime (Boolean. Optional, defaults to true)

If true, use local time. Otherwise, UTC is used. This parameter is
overwritten by the `utc` parameter.

### timezone (String. Optional)

By setting this parameter, one can parse the time value in the specified
timezone. The following formats are accepted:

1.  \[+-\]HH:MM (e.g. "+09:00")
2.  \[+-\]HHMM (e.g. "+0900")
3.  \[+-\]HH (e.g. "+09")
4.  Region/Zone (e.g. "Asia/Tokyo")
5.  Region/Zone/Zone (e.g. "America/Argentina/Buenos\_Aires")

The timezone set in this parameter takes precedence over
`localtime`\*\*, e.g., if `localtime` is set to `true` but `timezone` is
set to `+0000`, UTC would be used.

Example
-------

``` {.CodeRay}
format csv
fields host,method
```

With this configuration:

``` {.CodeRay}
tag:    app.event
time:   1362020400
record: {"host":"192.168.0.1","size":777,"method":"PUT"}
```

This incoming event is formatted to:

``` {.CodeRay}
"192.168.0.1","PUT"\n
```

With `force_quotes false`, the result is:

``` {.CodeRay}
192.168.0.1,PUT\n
```


Last updated: 2018-11-06 18:17:06 +0000
------------------------------------------------------------------------
Versions \| [v1.0 (td-agent3)](/v1.0/articles/formatter_csv) \|
***v0.12* (td-agent2) **
------------------------------------------------------------------------

If this article is incorrect or outdated, or omits critical information,
please [let us
know](https://github.com/fluent/fluentd-docs/issues?state=open).
[Fluentd](http://www.fluentd.org/) is a open source project under [Cloud
Native Computing Foundation (CNCF)](https://cncf.io/). All components
are available under the Apache 2 License.