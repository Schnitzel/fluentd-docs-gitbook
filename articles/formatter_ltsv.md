# ltsv Formatter Plugin

The `ltsv` formatter plugin output an event as [LTSV](http://ltsv.org).

``` {.CodeRay}
field1[label_delimiter]value1[delimiter]field2[label_delimiter]value2\n
```


## Parameters

-   [Common Parameters](/articles/plugin-common-parameters.md)
-   [Format section configurations](/articles/format-section.md)


### delimiter

    type     default     version
  -------- ------------ ---------
   string   "\\t"(TAB)   0.14.0

Delimiter for fields.

[]{#label_delimiter}

### label\_delimiter

    type    default   version
  -------- --------- ---------
   string      :      0.14.0

Delimiter for key value field.

[]{#add_newline}

### add\_newline

   type   default   version
  ------ --------- ---------
   bool    true     0.14.12

Add `\n` to the result.


## Example

``` {.CodeRay}
tag:    app.event
time:   1362020400
record: {"host":"192.168.0.1","size":777,"method":"PUT"}
```

This incoming event is formatted to:

``` {.CodeRay}
host:192.168.0.1\tsize:777\tmethod:PUT\n
```


------------------------------------------------------------------------

If this article is incorrect or outdated, or omits critical information,
please [let us know](https://github.com/fluent/fluentd-docs/issues?state=open).
[Fluentd](http://www.fluentd.org/) is a open source project under [Cloud
Native Computing Foundation (CNCF)](https://cncf.io/). All components
are available under the Apache 2 License.