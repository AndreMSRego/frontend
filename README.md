# Front-end - Guideline

The following document describes generic rules of writing in development language that we use on our Front-end project, that HTML, CSS, Typescript and React.

The idea of this repository is not to be a complete guideline, the target is just to help developers who participate in our projects to be able to inform the coding standards used.

As this is a live document, some rules may not have been applied in old projects and changes can occur at any time.

<a name="summary"></a>

## 📖 Summary

1. [General Code Patterns](#general-patterns)
2. [Architecture](#architecture)
3. [Git](#git)
4. [HTML](#html)
5. [CSS](#css)
6. [JavaScript](#javascript)
7. [TypeScritpt](#typescript)
8. [React](#react)
9. [Testing](#testing)

---

<a name="general-patterns"></a>

## 1. General Code Patterns

- 1.1 [Code Syntax](#code-syntax) <br>

<a name="code-syntax"></a>

### 1.1 Code Syntax

Use soft tabs with two spaces. You need to configure your editor for this.

**✅ Good:**

```js
const obj = {
  prop: "value",
  prop2: "value2",
  prop3: "value3",
}
```

```css
.foo {
  color: red;
}
```

```html
<div>
  <p>Hello World</p>
</div>
```

**❌ Bad:**

```js
const obj = {
    prop: "value",
    prop2: "value2",
    prop3: "value3",
}
```

```css
.foo {
    color: red;
}
```

```html
<div>
    <p>Hello World</p>
</div>
```

<a name="architecture"></a>

## 2. Architecture

The proper architecture for projects, and how to create and name files and folders.

- 2.1 [File Name](#architecture-files)
- 2.2 [Folder Architecture](#architecture-folder)

<a name="architecture-files"></a>

### 2.1 File Name

**✅ Good:**

- `components/TabsHeader/index.tsx`
- `components/TabsHeader/styles.ts`
- `components/TabsHeader/test.tsx`
- `templates/Registration/styles.ts`
- `pages/IntegrationErrors/index.tsx`

**❌ Bad:**

- `components/TabsHeader/TabsHeader.tsx`
- `src/TabsHeader.test.ts`
- `templates/Registration.tsx`
- `pages/IntegrationErrors.tsx`

<a name="architecture-folder"></a>

### 2.2 Folder Architecture

#### Global Components/Helpers

Global Components should only be components used in more than one module.

For example:

```sh
┣ 📂 src/components \
┣ ┣ 📂 componentName \
┣ ┃ ┣ 📜 index.tsx
┣ ┃ ┣ 📜 styles.ts
┣ ┃ ┣ 📜 test.tsx

```

#### Scoped Components/Helpers

We need to add inside `modules/**/components`, for example, all components that is need used just a context or scope, like a components that be used just a some place or specific page.

If we need to used the component again in another context or page it need to be moved to `src/components`.

For example:

```sh
┣ 📂 modules \
┣ ┣ 📂 CustomerRegistration \
┣ ┃ ┣ 📂 components \
┣ ┃ ┃ ┣ 📂 Divider \
┣ ┣ ┃ ┃ ┣ 📜 index.tsx \
┣ ┣ ┃ ┃ ┣ 📜 test.tsx \
```

**[⬆ back to summary](#summary)**

---

<a name="git"></a>

## 3. Git

- 3.1 [Commit Messages](#commit-messages) <br>

<a name="commit-messages"></a>

### 3.1 Commit Messages

In order to facilitate the contribution of anyone in a project, all commit messages must be in **English**.

We also use [conventional commit messages](https://www.conventionalcommits.org/en/v1.0.0/), that is, the commit message must be in the form of a sentence, with the first word being an action, and the rest of the sentence a describing text.

**✅ Good:**

```powershell
git commit -m "feat: allow provided config object to extend configs"
git commit -m "docs: correct spelling of CHANGELOG"
git commit -m "feat(lang): add the Portuguese language"
```

**❌ Bad:**

```powershell
git commit -m "Add placeholder on input"
```

**[⬆ back to summary](#summary)**

---

<a name="html"></a>

## 4. HTML

<a name="html"></a>

We main reference for HTML good patterns is [W3C](https://www.w3.org/TR/html/) and [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element), behind these docs we could learn a lot with semantic and another good practices.

- 4.1 [HTML Component Scope](#html-component-scope)

<a name="html-component-scope"></a>

We don't guest the scope of HTML components inside page, so when we start a new component, we should use a semantic tag, like `section` or `article` for example, to be able to starting to use the heading tags by context.

**✅ Good:**

```html
<section class="component">
  <h1 class="title">Title</h1>
  <p>Paragraph</p>
</section>
```

**❌ Bad:**

```html
<div class="component">
  <h4 class="title">Title</h4>
  <p>Paragraph</p>
</div>
```

<a name="css"></a>

## 5. CSS

The tips above could be used in any CSS framework or preprocessor, like SCSS, Styled Components and etc

- 5.1 [CSS Code Syntax](#css-syntax)
- 5.2 [CSS Declaration Order](#css-order)
- 5.3 [CSS Class Names](#css-class-name)
- 5.4 [CSS Good Practices](#css-good-practices)

<a name="css-syntax"></a>

### 5.1 CSS Syntax

Keep one declaration per line.

**✅ Good:**

```scss
.selector-1,
.selector-2,
.selector-3 {
  ...
}
```

**❌ Bad:**

```scss
.selector-1, .selector-2, .selector-3 {
  ...
}
```

Separate each ruleset by a blank line.

**✅ Good:**

```scss
.selector-1 {
  ...
}

.selector-2 {
  ...
}
```

**❌ Bad:**

```scss
.selector-1 {
  ...
}
.selector-2 {
  ...
}
```

Use lowercase and avoid specifying units is zero-values.

**✅ Good:**

```scss
.selector-1 {
  color: #aaaaaa;
  margin: 0;
}
```

**❌ Bad:**

```scss
.selector-1 {
  color: #aaaaaa;
  margin: 0px;
}
```

<a name="css-order"></a>

### 5.2 CSS Declaration Order

The declarations should be added in alphabetical order.

**✅ Good:**

```scss
.selector {
  background: #fff;
  border: #333 solid 1px;
  color: #333;
  display: flex;
  height: 200px;
  margin: 5px;
  padding: 5px;
  width: 200px;
}
```

**❌ Bad:**

```scss
.selector {
  padding: 5px;
  height: 200px;
  background: #fff;
  margin: 5px;
  width: 200px;
  color: #333;
  border: #333 solid 1px;
  display: flex;
}
```

<a name="css-class-name"></a>

### 5.3 CSS Class Names

Keep class lowercase and use dashes to separate the classname.

**✅ Good:**

```scss
.page-header { ... }
```

**❌ Bad:**

```scss
.pageHeader { ... }
.page_header { ... }
```

Is a good idea follows a [BEM naming convention](http://getbem.com/introduction/) to avoid conflicts with other components. If you are using CSS-in-JS like a Styled-Component, you can use BEM if you need to nesting elements inside parent.

The main pattern is use single dash to element name, double underline to element block and double dash to style modification.

**✅ Good:**

```scss
/* Good */
.page-header__title { ... }
.page-header--active { ... }

.button--active { ... }
```

**❌ Bad:**

```scss
.page-header-title { ... }
.page-header-active { ... }

.active { ... }
.primary { ... }
```

Dashes and underline serve as natural breaks in related class. Prefix class based on the closest parent or base class.

**✅ Good:**

```scss
.nav { ... }
.nav__item { ... }
.nav__link { ... }
```

**❌ Bad:**

```scss
.item-nav { ... }
.link-nav { ... }
```

Avoid giving too short names for class and always choose meaningful names that provide the class function.

**✅ Good:**

```scss
/* Good */
.button { ... }
.page-header { ... }
.progress-bar { ... }
```

**❌ Bad:**

```scss
.s { ... }
.btn { ... }
.ph { ... }
.block { ... }
```

<a name="css-good-practices"></a>

### 5.4 CSS Good Practices

Never use IDs to style elements, always use classes instead.

**✅ Good:**

```scss
.header { ... }
.section { ... }
```

**❌ Bad:**

```scss
#header { ... }
#section { ... }
```

Do not style directly the elements, it will create a lot of conflicts, always use classes instead.

**✅ Good:**

```scss
.form-control { ... }
.header { ... }
.section { ... }
```

**❌ Bad:**

```scss
input[type="text"] { ... }
header
section
```

Avoid nesting elements, because it decrease performance and increase the specificity of the CSS, always use classes instead.

**✅ Good:**

```scss
.navbar { ... }
.nav { ... }
.nav__item { ... }
.nav__link { ... }
```

**❌ Bad:**

```scss
.navbar ul { ... }
.navbar ul li { ... }
.navbar ul li a { ... }
```

**[⬆ back to summary](#summary)**

<a name="javascript"></a>

## 6. JavaScript

- 6.1 [Javascript Code Syntax](#javascript-syntax)
- 6.2 [Variables](#variables) <br>
- 6.3 [Descriptive validations (if)](#descriptive-validations) <br>
- 6.4 [Avoid multiple if's](#avoid-multiple-ifs) <br>

<a name="javascript-syntax"></a>

### 6.1 JavaScript Code Syntax

Always use single quotes or template literals

**✅ Good:**

```js
const string = 'foo'
const template = `foo`
```

**❌ Bad:**

```js
const string = "foo"
const template = "foo"
```

<a name="variables"></a>

For strict equality checks `===` should be used in favor of `==`.

**✅ Good:**

```js
if (foo === "foo") {
  statement
}
```

**❌ Bad:**

```js
if (foo == "foo") {
  statement
}
```

### 6.2 Variables

Use meaningful, pronounceable, and in **English** variable names.

**✅ Good:**

```js
const currentDate = new Date().toLocaleDateString("pt-BR")
```

**❌ Bad:**

```js
const xpto = new Date().toLocaleDateString("pt-BR")
```

<a name="descriptive-validations"></a>

### 6.3 Descriptive validations (if)

Creating const to describe validations.

**✅ Good:**

```js
const hasFullUserName = user.firstName && user.lastname

if (hasFullUserName) {
  //do awesome something
}
```

**❌ Bad:**

```js
if (user.firstName && user.lastname) {
  //do something
}
```

<a name="avoid-multiple-ifs"></a>

### 6.4 Avoid multiple if's

Use an execution map instead a multiple if validations.

**✅ Good:**

```js
const messagingChannels = {
  whatsapp: (message) => {
    // send message to whatsapp
  },
  email: (message) => {
    // send message to email
  }
}

const sendMessage = (message, channel) => {
  const send = messagingChannels[channel];
  return send && send(message);
}
```

**❌ Bad:**

```js
const sendWhatsapp = (message) => {
  // send message to whatsapp
}

const sendEmail = (message) => {
  // send message to email
}

const sendMessage = (message, channel) => {
  if (channel === 'whatsapp') {
    sendWhatsapp(message)
  } else if (channel === 'email') {
    sendEmail(message)
  }
}
```

**[⬆ back to summary](#summary)**

---

<a name="typescript"></a>

## 7. TypeScript

- 6.1 [Primitive Types](#typescript-primitive-types)
- 6.2 [Type Inference](#type-inference) <br>
- 6.3 [Avoid any ](#avoid-any) <br>

<a name="typescript-primitive-types"></a>

### 6.1 Primitive Types

 Prefer to use primitive types

**✅ Good:**

```ts
function reverse(s: string): string;
interface Person {
  name: string;
  age: number;
  active: boolean;
}
```

**❌ Bad:**

```ts
function reverse(s: String): String;
interface Person {
  name: String;
  age: Number;
  active: Boolean;
}
```

<a name="type-inference"></a>

### 6.2 Type Inference

Instead of explicitly declaring the type, let the compiler automatically infer the type for you.

**✅ Good:**

```ts
const [loading, setLoading] = useState(false) //loading is boolean
const personName = 'Andre' //personName is string
```

**❌ Bad:**

```js
const [loading, setLoading] = useState<boolean>(false)
const personName: string = 'Andre'
```

<a name="descriptive-validations"></a>

### 6.3 Avoid any

Use correct data type annotation.

**✅ Good:**

```ts
interface Customer {
  id: string;
  document: string;
  hasInvestments: boolean;
}
```

**❌ Bad:**

```js
interface Customer {
  id: any;
  document: any;
  hasInvestments: any;
}
```

**[⬆ back to summary](#summary)**

---

<a name="react"></a>

## 7. React

- 7.1 [Keys in lists](#keys-in-lists-react)
- 7.2 [useState functional updates](#usestate-functional-updates) <br>
- 7.3 [useEffect dependencies array](#useeffect-dependencies-array) <br>
- 7.4 [Readable components](#readable-components) <br>

<a name="keys-in-lists-react"></a>

### 7.1 Keys in lists

The best way to pick a key is to use a string that uniquely identifies a list item among its siblings.

It is not recommended to use indexes for keys if the order of items can change. This can negatively affect performance and can cause problems with the component's state.

**✅ Good:**

```js
array.map((item, index) => <Component key={item.id} {...item}>)
```

**❌ Bad:**

```js
array.map((item, index) => <Component key={index} {...item}>)
```

<a name="usestate-functional-updates"></a>

### 7.2 useState functional updates

If the new state is calculated using the previous state, you can pass a function to setState. Thus avoiding competition between states and preventing possible bugs.

**✅ Good:**

```js
const [number, setNumber] = useState(1)

return (
  <div>
    <h1>{number}</h1>
    <button onClick={() => setNumber((prevNumber) => prevNumber + 1)}>
      Increase
    </button>
    <button onClick={() => setNumber((prevNumber) => prevNumber - 1)}>
      Decrease
    </button>
  </div>
)
```

**❌ Bad:**

```js
const [number, setNumber] = useState(1)

return (
  <div>
    <h1>{number}</h1>
    <button onClick={() => setNumber(number + 1)}>Increase</button>
    <button onClick={() => setNumber(number - 1}>Decrease</button>
  </div>
)
```

<a name="useeffect-dependencies-array"></a>

### 7.3 useEffect dependencies array

Use the useEffect dependency array to trigger side effects, and make your code cleaner.

**✅ Good:**

```js
const [page, setPage] = useState(1)

useEffect(() => {
  requestListUser()
  // calls useEffect when page state changes
}, [page])

return (
  <div>
    <button onClick={() => setPage((prevState) => prevState + 1)}>
      Next Page
    </button>
  </div>
)
```

**❌ Bad:**

```js
const [page, setPage] = useState(1)

useEffect(() => {
  requestListUser()
}, [])

const requestListUser = () => {
  setPage((prevState) => prevState + 1)
  // ...
  // any code to return user list
}

return (
  <div>
    <button onClick={() => requestListUser()}>Next Page</button>
  </div>
)
```

<a name="readable-components"></a>

### 7.4 Readable components

Avoid creating very large components.
If possible divided into sub-components, improving the understanding and reading of the code.

**✅ Good:**

```js
const Screen = () => (
  <Container>
    <Header>
      <Title />
      <Button background="black">Filter</Button>
    </Header>

    <Main>
      <List>
        {data.map((item) => (
          <Card key={item.id} name={item.name} />
        ))}
      </List>
    </Main>
  </Container>
)
```

**❌ Bad:**

```js
const Screen = () => (
  <Box padding={1}>
    <Box alignItems="center">
      <Text>Titulo</Text>
      <Button background="black">Filter</Button>
    </Box>
    <Box marginTop={5}>
      <Box>
        {data.map((item) => (
          <Box key={item.id}>
            <Text color="red">{item.name}</Text>
          </Box>
        ))}
      </Box>
    </Box>
  </Box>
)
```


**[⬆ back to summary](#summary)**

---

## 10. Testing

- 10.1 [Write tests with "it"](#tests-with-it)

<a name="tests-with-it"></a>

### 10.1 Write tests with "it"

Write tests with the alias "it" instead "test" method.

**✅ Good:**

```js
describe('yourModule', () => {
  it('should do this thing', () => {});
});
```

**❌ Bad:**

```js
describe('yourModule', () => {
  test('if it does this thing', () => {});
});
```

**[⬆ back to summary](#summary)**

---
