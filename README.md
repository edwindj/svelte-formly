<p align="center">
  <img width="100%" height="300" src="./logo.png" alt="Svelte Formly" />
</p>

# Svelte Formly

by [@kamalkech](https://github.com/kamalkech)

[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](http://standardjs.com) [![CircleCI](https://circleci.com/gh/beyonk-adventures/svelte-component-livereload-template.svg?style=shield)](https://circleci.com/gh/beyonk-adventures/svelte-component-livereload-template) [![svelte-v3](https://img.shields.io/badge/svelte-v3-blueviolet.svg)](https://svelte.dev)

## Features

- ⚡️ Generate Forms
- 😍 Easy to extend with custom field type, validation, wrapper and extension.

## Installation

npm i svelte-formly

## Usage

```javascript
<script>
  import { onDestroy } from "svelte";
  import { valuesForm, Field } from "svelte-formly";

  let message = "";

  const fields = [
    {
      type: "text",
      name: "firstname",
      value: "",
      id: "firstname",
      placeholder: "Tap your first name",
      validation: ["required", "min:6"]
    },
    {
      type: "text",
      name: "lastname",
      value: "",
      id: "lastname",
      placeholder: "Tap your lastname"
    },
    {
      type: "email",
      name: "email",
      value: "",
      id: "email",
      placeholder: "Tap your email",
      validation: ["required", "email"]
    }
  ];

  function onSubmit() {
    valuesForm.subscribe(data => {
      if (data.isValidForm) {
        message = "Congratulation! now your form is valid";
      } else {
        message = "Your form is not valid!";
      }
    });
  }

  onDestroy(valuesForm);
</script>
```

```html
<h2>{message}</h2>
<form on:submit|preventDefault="{onSubmit}" novalidate>
  <Field {fields} />
  <button class="btn btn-primary" type="submit">Submit</button>
</form>
```
