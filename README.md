# Intro

This project integrates the Gup Design System web components into Angular. By using the web components approach, the components remain framework-agnostic, making it easier to integrate into different frontend frameworks or libraries.

## Web Components Setup

Import Web Components in index.html: Web components need to be imported directly into the index.html file. This can be done by including the following script in the <head> tag of src/index.html:
```html
<script type="module" src="https://develop.omangup.me/nexus/repository/gup-raw-repo/gup-ds-components/latest/components.js"></script>
```
## Importing Styles

To maintain a consistent look and feel across the project, the Gup Design System styles can be imported. You can include global CSS styles for the components in your src/styles.css or src/styles.scss file:

```css
@import url('https://develop.omangup.me/nexus/repository/gup-raw-repo/gup-ds-components/latest/styles.css');
```

## Configure Angular to Recognize Custom Elements

In src/app/app.module.ts, add the CUSTOM_ELEMENTS_SCHEMA to the schemas array:

```ts
import { NgModule, CUSTOM_ELEMENTS_SCHEMA } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule],
  providers: [],
  bootstrap: [AppComponent],
  schemas: [CUSTOM_ELEMENTS_SCHEMA],  // Added this line
})
export class AppModule {}
```

## TypeScript Configuration for Custom Elements

By default, TypeScript will throw errors when it encounters unknown HTML tags (like custom web components). To suppress these errors, a custom TypeScript declaration file was created at src/custom-elements.d.ts:

```ts
declare namespace JSX {
  interface IntrinsicElements {
    [elemName: `gup-${string}`]: any;
  }
}
```

## Usage

Once the setup is complete, you can use Gup web components in your Angular components just like any other HTML elements.

```html
<gup-input-field label="Enter your email" type="email" placeholder="Email"></gup-input-field>
<gup-button label="Submit"></gup-button>
```
