# Chakra UI Bindings for react-hook-form

Bindings for using [react-hook-form](https://github.com/react-hook-form/react-hook-form) with [Chakra UI](http://next.chakra-ui.com).

[![alt Version](https://img.shields.io/npm/v/chakra-ui-react-hook-form?color=blue)](https://www.npmjs.com/package/chakra-ui-react-hook-form)
[![alt License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
![npm](https://img.shields.io/npm/dt/react-hook-form-chakra-ui)

## Getting started

`yarn add @chakra-ui/react @emotion/react @emotion/styled framer-motion react-hook-form chakra-ui-react-hook-form`

Or

`npm i @chakra-ui/react @emotion/react @emotion/styled framer-motion react-hook-form chakra-ui-react-hook-form`

```jsx
import * as Yup from 'yup';
import { yupResolver } from '@hookform/resolvers/yup';
import {
  InputControl,
  NumberInputControl,
  TextareaControl,
  SubmitButton,
} from 'chakra-ui-react-hook-form';
import { useForm } from 'react-hook-form';

const infoFormValidationSchema = Yup.object({
  firstName: Yup.string().required(),
  lastName: Yup.string().required(),
  description: Yup.string().required(),
  age: Yup.number().required(),
});

type InfoFormValues = Yup.InferType<typeof infoFormValidationSchema>;

const InfoForm = () => {
  const { control, handleSubmit } = useForm<InfoFormValues>({
    defaultValues: {
      firstName: '',
      lastName: '',
      description: '',
      age: 0,
    },
    resolver: yupResolver(infoFormValidationSchema),
  });

  const onSubmit = (values: InfoFormValues) => {
    console.log({ values });
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <InputControl control={control} name="firstName" label="First name:" />
      <InputControl control={control} name="lastName" label="Last name:" />
      <NumberInputControl control={control} name="age" label="Age:" />
      <TextareaControl control={control} name="description" label="Description:" />
      <SubmitButton control={control} />
    </form>
  );
};
```

## Roadmap

### Components

- [x] Input (`valueAsNumber`, `valueAsDate`, `setValueAs`)
- [x] Textarea
- [x] Checkbox (`<CheckboxGroup/>`)
  - [] Standalone `<Checkbox>`
- [x] Number Input
- [x] Radio (`<RadioGroup/>`)
- [x] Select
- [] Progress
- [] Pin Input

### Utility Components

- [x] Submit button

### Extras

- [] File input
- [] Image input (zoom & crop)