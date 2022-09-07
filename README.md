## description

Trying to minimally reproduce an issue where `buf breaking` apparently thinks files have been deleted when they have not:

```
> buf breaking --path protos/etsy/example/math --against '.git#branch=main' --error-format json
{"type":"FILE_NO_DELETE","message":"Previously present file \"protos/etsy/example/math/v1/math.proto\" was deleted."}
{"path":"protos/etsy/example/math/v1/math.proto","start_line":16,"start_column":5,"end_line":16,"end_column":32,"type":"FIELD_SAME_TYPE","message":"Field \"2\" on message \"AdderRequest\" changed type from \"google.protobuf.UInt64Value\" to \"google.protobuf.StringValue\"."}
```

To test in this repo:

```
> buf breaking --against '.git#branch=main' --error-format json
```
