# JSON Strip Comments

A fork of a fork for stripping JSON comments and trailing commas in place:

* https://github.com/tmccombs/json-comments-rs
* https://github.com/parcel-bundler/parcel/pull/9032

## Example

```rust
use serde_json::Value;

fn main() {
    let mut data = String::from(
        r#"
     {
         "name": /* full */ "John Doe",
         "age": 43,
         "phones": [
             "+44 1234567", // work phone
             "+44 2345678", // home phone
         ]
     }"#,
    );

    json_strip_comments::strip(&mut data).unwrap();
    let value: Value = serde_json::from_str(&data).unwrap();

    println!("{value}");
}
```
