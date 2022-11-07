# SPARCS Taxi - React Mobile Picker

## Preview

Visit (in mobile or mobile simulator): [sparcs-kaist.github.io/taxi-react-mobile-picker](https://sparcs-kaist.github.io/taxi-react-mobile-picker/)

## Install

```
npm install taxi-react-mobile-picker --save
```

## Usage

### ES6

```javascript
import Picker from "taxi-react-mobile-picker";
```

### CommonJS

```javascript
const Picker = require("taxi-react-mobile-picker");
```

## Props

| Property name         | Type     | Default | Description                                                                                                  |
| --------------------- | -------- | ------- | ------------------------------------------------------------------------------------------------------------ |
| optionGroups          | Object   | N/A     | Key-value pairs as `{name1: options1, name2: options2}`. `options` is an array of all options for this name. |
| valueGroups           | Object   | N/A     | Selected value pairs as `{name1: value1, name2: value2}`.                                                    |
| onChange(name, value) | Function | N/A     | Callback called when user pick a new value.                                                                  |
| onClick(name, value)  | Function | N/A     | Callback called when user click on selected value.                                                           |
| itemHeight            | Number   | 36      | Height of each item (that is each option). In `px`.                                                          |
| height                | Number   | 216     | Height of the picker. In `px`.                                                                               |

## Getting Started

By design, React Mobile Picker is a [Controlled Component](https://facebook.github.io/react/docs/forms.html#controlled-components), which means the selected value of the rendered element will always reflect the `valueGroups`. Every time you want to change the selected item, just modify `valueGroups` values.

Here is an example of how to integrate React Mobile Picker:

```javascript
import React, { Component } from "react";
import Picker from "taxi-react-mobile-picker";

class App extends Component {
  constructor(props) {
    super(props);
    this.state = {
      valueGroups: {
        title: "Mr.",
        firstName: "Micheal",
        secondName: "Jordan",
      },
      optionGroups: {
        title: ["Mr.", "Mrs.", "Ms.", "Dr."],
        firstName: ["John", "Micheal", "Elizabeth"],
        secondName: ["Lennon", "Jackson", "Jordan", "Legend", "Taylor"],
      },
    };
  }

  // Update the value in response to user picking event
  handleChange = (name, value) => {
    this.setState(({ valueGroups }) => ({
      valueGroups: {
        ...valueGroups,
        [name]: value,
      },
    }));
  };

  render() {
    const { optionGroups, valueGroups } = this.state;

    return (
      <Picker
        optionGroups={optionGroups}
        valueGroups={valueGroups}
        onChange={this.handleChange}
      />
    );
  }
}
```

## License

MIT.
