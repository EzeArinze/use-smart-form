# 🧠 useSmartForm

A powerful, schema-aware, developer-friendly React form utility built on top of `react-hook-form`. Supports Zod schemas, dynamic field rendering, conditional logic (`showWhen`), and much more — with a clean, declarative API. install zod react-hook-form if not installed automatically

---

## ✨ Features

- ✅ Minimal boilerplate
- 🔐 Schema validation with [Zod](https://zod.dev/)
- 📦 Built on `react-hook-form`
- 🧠 Conditional fields with `showWhen`
- 🎛 Reusable `Field` component
- 🧼 Auto-reset & clean form context
- 🎨 Tailwind-ready UI (customizable)
- ⚡ Full TypeScript support

---

## 📦 Installation

```bash
npm install use-smart-form
```

or

```bash
yarn install use-smart-form
```

```bash
import { useSmartForm, SmartForm, SmartField } from "use-smart-form";
import { z } from "zod";

const schema = z.object({
  name: z.string().min(1, "Name is required"),
  email: z.string().email("Invalid email"),
  age: z.number().optional(),
  wantsNewsletter: z.boolean(),
  newsletterFrequency: z.string().optional(),
});

export default function ExampleForm() {
   const { Form, Field, reset } = useSmartFormV2({
    schema,
    onSubmit: (values) => console.log(values),
  });

  return (
    <div className="min-h-screen flex items-center justify-center bg-gradient-to-br from-blue-100 to-purple-200">
      <div className="shadow-xl rounded-xl p-8 w-full max-w-md">
        <Form>
          <Field name="name" label="Name" placeholder="Enter name" />
          <Field name="age" label="Age" type="number" placeholder="age" />
          <Field
            name="email"
            label="Email Address"
            type="email"
            placeholder="Enter Email Address"
          />
          <Field
            name="mood"
            label="Select your mood"
            type="select"
            options={["Happy", "Sad"]}
          />
          <Field
            name="bio"
            label="Bio"
            type="textarea"
            placeholder="Tell us about yourself"
            rows={1}
          />
          <div>
            <Field
              name="isStudent"
              type="checkbox"
              checkBoxLabel="Are you a student"
            />
          </div>
          <div className="flex justify-center mt-6">
            <button className="shadow-xs hover:bg-primary/90">Submit</button>
          </div>
        </Form>
      </div>
    </div>
  );
}
```

## 🧩 API

useSmartForm({ schema, onSubmit })

- Return Description
- Form Form wrapper component
- Field Smart form field renderer
- reset() Resets the form to default values

### Props:

| Prop            | Type                                                                    | Description                   |
| --------------- | ----------------------------------------------------------------------- | ----------------------------- |
| `name`          | `string`                                                                | Field name (required)         |
| `label`         | `string`                                                                | Label text                    |
| `type`          | `"text"`, `"email"`, `"number"`, `"select"`, `"textarea"`, `"checkbox"` | Field type (defaults to text) |
| `options`       | `string[]`                                                              | For `select` fields           |
| `placeholder`   | `string`                                                                | Input placeholder             |
| `rows`          | `number`                                                                | For `textarea`                |
| `checkBoxLabel` | `string`                                                                | Label next to checkbox        |
| `showWhen`      | `eg: showWhen={(values) => values.isStudent}`                           | Conditionally render field    |

### 💅 Styling

- Built with Tailwind-compatible markup (className support)
- Use clsx or tailwind-merge to customize field wrappers and inputs
- You can override the internal field renderer via component

### 🔐 Validation

- Supports Zod out of the box. Errors are displayed inline, mapped automatically from the schema.

```bash
const schema = z.object({
  email: z.string().email("Must be a valid email"),
});

```

# 👨‍💻 Author

Made with 💙 by @eze-arinze

## 🚧 Roadmap (things that can be done in the future)

- Field arrays support

- Stepper / Wizard form flow

- Custom component overrides

- Theme system
