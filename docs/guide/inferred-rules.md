# Inferred Rules

While you can specify your rules in the `v-validate` directive, vee-validate also deduces or infers additional rules based on the input type. For example if you have the following:

```html
<input
  name="email"
  type="email"
  required
>
```

It would be redundant to specify `v-validate="'required|email'"`. vee-validate will detect the input type and the required attribute and include those rules for you automatically, so you would only need to add `v-validate` on the input.

```html
<input
  name="email"
  type="email"
  required
  v-validate
>
```

## Inferred Rules Reference

This is a table of HTML attributes that is inferred as rules.

| Attribute Name |   value      | Rule           |
| ------------- |:-------------:| -------- |
| type      | "email" |  `email`  |
| type      | "number"  | `decimal`  |
| type | "date" | `date_format:YYYY-MM-DD` |
| type | "datetime-local" | `date_format: YYYY-MM-DDThh:mm` |
| type | "time" | `date_format:hh:mm` or `date_format:hh:mm:ss` depending on the step value |
| type | "week" | `date_format:YYYY-Www` |
| type | "month | `date_format:YYYY-MM` |
| min | val |  min_value: val |
| max | val | max_value: val |
| pattern | rgx | regex: rgx |

::: tip
  This feature does not work on custom components, only HTML5 inputs can take advantage from this feature.
:::