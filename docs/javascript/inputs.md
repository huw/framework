# JavaScript: Inputs

You can use the built-in [`view` function](#view(input)) and an HTML input element to create a reactive input. For example, here is a slider:

```js show
const gain = view(Inputs.range([0, 11], {value: 5, step: 0.1, label: "Gain"}));
```

Now you can reference the input’s value (here `gain`) anywhere. The code will run whenever the input changes; no event listeners required!

```md
The current gain is ${gain.toFixed(1)}!
```

The current gain is ${gain.toFixed(1)}!

## view(*input*)

As described above, this function [displays](./display) the given input element and then returns its corresponding [generator](./generators) via `Generators.input`. Use this to display an input element while also exposing the input’s value as a [reactive top-level variable](./reactivity).

## Built-in inputs

These basic inputs will get you started.

* [Button](#button) - do something when a button is clicked
* [Toggle](#toggle) - toggle between two values (on or off)
* [Checkbox](#checkbox) - choose any from a set
* [Radio](#radio) - choose one from a set
* [Range](#range) or [Number](https://observablehq.com/@observablehq/input-range) - choose a number in a range (slider)
* [Select](#select) - choose one or any from a set (drop-down menu)
* [Text](#text) - enter freeform single-line text
* [Textarea](#textarea) - enter freeform multi-line text
* [Date](#date) or [Datetime](https://observablehq.com/@observablehq/input-date) - choose a date
* [Color](#color) - choose a color
* [File](#file) - choose a local file

These fancy inputs are designed to work with tabular data such as CSV or TSV [file attachments](./files).

* [Search](#search) - query a tabular dataset
* [Table](#table) - browse a tabular dataset

---

### Button

Do something when a button is clicked. [Examples ›](https://observablehq.com/@observablehq/input-button) [API Reference ›](https://github.com/observablehq/inputs/blob/main/README.md#button)

```js show
const clicks = view(Inputs.button("Click me"));
```

```js
clicks
```

---

### Toggle

Toggle between two values (on or off). [Examples ›](https://observablehq.com/@observablehq/input-toggle) [API Reference ›](https://github.com/observablehq/inputs/blob/main/README.md#toggle)

```js show
const mute = view(Inputs.toggle({label: "Mute"}));
```

```js
mute
```

---

### Checkbox

Choose any from a set. [Examples ›](https://observablehq.com/@observablehq/input-checkbox) [API Reference ›](https://github.com/observablehq/inputs/blob/main/README.md#checkbox)

```js show
const flavors = view(Inputs.checkbox(["salty", "sweet", "bitter", "sour", "umami"], {label: "Flavors"}));
```

```js
flavors
```

---

### Radio

Choose one from a set. [Examples ›](https://observablehq.com/@observablehq/input-radio) [API Reference ›](https://github.com/observablehq/inputs/blob/main/README.md#radio)

```js show
const flavor = view(Inputs.radio(["salty", "sweet", "bitter", "sour", "umami"], {label: "Flavor"}));
```

```js
flavor
```

---

### Range

Pick a number. [Examples ›](https://observablehq.com/@observablehq/input-range) [API Reference ›](https://github.com/observablehq/inputs/blob/main/README.md#range)

```js show
const n = view(Inputs.range([0, 255], {step: 1, label: "Favorite number"}));
```

```js
n
```

---

### Select

Choose one, or any, from a menu. [Examples ›](https://observablehq.com/@observablehq/input-select) [API Reference ›](https://github.com/observablehq/inputs/blob/main/README.md#select)

```js
const capitals = FileAttachment("us-state-capitals.tsv").tsv({typed: true});
const stateNames = capitals.then((capitals) => capitals.map(d => d.State));
```

```js show
const homeState = view(Inputs.select([null].concat(stateNames), {label: "Home state"}));
```

```js
homeState
```

```js show
const visitedStates = view(Inputs.select(stateNames, {label: "Visited states", multiple: true}));
```

```js
visitedStates
```

---

### Text

Enter freeform single-line text. [Examples ›](https://observablehq.com/@observablehq/input-text) [API Reference ›](https://github.com/observablehq/inputs/blob/main/README.md#text)

```js show
const name = view(Inputs.text({label: "Name", placeholder: "What’s your name?"}));
```

```js
name
```

---

### Textarea

Enter freeform multi-line text. [Examples ›](https://observablehq.com/@observablehq/input-textarea) [API Reference ›](https://github.com/observablehq/inputs/blob/main/README.md#textarea)

```js show
const bio = view(Inputs.textarea({label: "Biography", placeholder: "What’s your story?"}));
```

```js
bio
```

---

### Date

Choose a date, or a date and time. [Examples ›](https://observablehq.com/@observablehq/input-date) [API Reference ›](https://github.com/observablehq/inputs/blob/main/README.md#date)

```js show
const birthday = view(Inputs.date({label: "Birthday"}));
```

```js
birthday
```

---

### Color

Choose a color. [Examples ›](https://observablehq.com/@observablehq/input-color) [API Reference ›](https://github.com/observablehq/inputs/blob/main/README.md#color)

```js show
const color = view(Inputs.color({label: "Favorite color", value: "#4682b4"}));
```

```js
color
```

---

### File

Choose a local file. [Examples ›](https://observablehq.com/@observablehq/input-file) [API Reference ›](https://github.com/observablehq/inputs/blob/main/README.md#file)

```js show
const file = view(Inputs.file({label: "CSV file", accept: ".csv", required: true}));
```

```js
data = file.csv({typed: true})
```

---

### Search

Query a tabular dataset. [Examples ›](https://observablehq.com/@observablehq/input-search) [API Reference ›](https://github.com/observablehq/inputs/blob/main/README.md#search)

```js show
const search = view(Inputs.search(capitals, {placeholder: "Search U.S. capitals"}));
```

```js
search // see table below!
```

---

### Table

Browse a tabular dataset. [Examples ›](https://observablehq.com/@observablehq/input-table) [API Reference ›](https://github.com/observablehq/inputs/blob/main/README.md#table)

```js show
const rows = view(Inputs.table(search));
```

```js
rows // click a checkbox in the leftmost column
```

---

* [Form](https://observablehq.com/@observablehq/input-form?collection=@observablehq/inputs) - combine multiple inputs for a compact display