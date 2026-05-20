# @dreams/phone-input-modern

A customizable React phone input component with country search, flags, preferred country codes, country-code detection, and formatted phone number output.

## Install

```bash
npm install @dreams/phone-input-modern
```

## Usage

```jsx
import { useState } from "react";
import PhoneInput from "@dreams/phone-input-modern";
import "@dreams/phone-input-modern/style.css";

export default function Example() {
  const [phoneValues, setPhoneValues] = useState({
    number: "",
    countryCode: "91",
    tempCountryCode: "91",
  });
  const [error, setError] = useState(null);

  return (
    <PhoneInput
      phoneValues={phoneValues}
      PreferredCountryCodes={["91", "971"]}
      defaultCountryCode="91"
      handlePhoneChange={setPhoneValues}
      error={error}
      setError={setError}
    />
  );
}
```

## Props

| Prop                                                                                                                                                      | Type        | Default          | Description                                                                                                                    |
| --------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | ---------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| `phoneValues`                                                                                                                                             | `object`    | Required         | Current phone state. Common keys are `number`, `countryCode`, `tempCountryCode`, `editNumber`, and `editCode`.                 |
| `handlePhoneChange`                                                                                                                                       | `function`  | `() => {}`       | Called with formatted phone data when the value changes.                                                                       |
| `PreferredCountryCodes`                                                                                                                                   | `string[]`  | `[]`             | Dialing codes to show at the top of the country list, for example `["91", "971"]`.                                             |
| `defaultCountryCode`                                                                                                                                      | `string`    | Auto-detect      | Initial dialing code, for example `"91"`. If omitted, the component tries to detect the country with `https://ipapi.co/json/`. |
| `setError`                                                                                                                                                | `function`  | `() => {}`       | Receives validation messages.                                                                                                  |
| `error`                                                                                                                                                   | `string`    | `undefined`      | Current error message from your app.                                                                                           |
| `CombinedToSeperate`                                                                                                                                      | `boolean`   | `false`          | Converts a combined code and phone number into separate values through `handlePhoneChange`.                                    |
| `dropdownArrow`                                                                                                                                           | `ReactNode` | Built-in arrow   | Custom dropdown icon.                                                                                                          |
| `containerCss`, `selectedFlagCss`, `selectedCountryCss`, `dropdownCss`, `searchInputCss`, `ulCss`, `PreferredliCss`, `filteredliCss`, `liCss`, `inputCss` | `string`    | Built-in classes | Class names for styling individual parts of the component.                                                                     |

## Returned Phone Data

`handlePhoneChange` receives an object like this:

```js
{
  countryCode: "91",
  number: "9876543210",
  tempCountryCode: "91",
  FormattedNumber: "98765 43210",
  countryCodeAndNumber: "919876543210",
  countryCodeAndFormattedNumber: "91 98765 43210",
  selectedCountry: {
    name: "India",
    code: "in",
    dialingCode: "91"
  }
}
```

## Publish

Before publishing, make sure you are logged in:

```bash
npm login
```

Then verify the package:

```bash
npm run build
npm pack --dry-run
```

Publish it:

```bash
npm publish --access public
```
