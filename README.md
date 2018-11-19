# Code Conventions

## Angular code conventions

The purpose of this style guide is to provide guidance on building Angular applications while standarizing some conventions that we have decided to use. Generally speaking you are not going to find anything different that what it is specified in the [Angular Style Guide](https://angular.io/guide/styleguide) by John Papa.

## Naming

### Naming Guidelines

  - Use consistent names for all components following a pattern that describes the component's feature then (optionally) its type. Recommended pattern is `feature.type.js`. There are 2 names for most assets:
    * the file name (`avengers.component.ts`)
    * the registered component name with Angular (`Component`)

### Feature File Names

  - Use consistent names for all components following a pattern that describes the component's feature then (optionally) its type. Recommended pattern is `feature.type.ts`.

### Test File Names

  - Name test specifications similar to the component they test with a suffix of `spec`.

### Component Names

  - Use consistent names for all components named after their feature. Use UpperCamelCase for components, as they are constructors.
  - Append the component name with the suffix `Component`.

    ```typescript
    /**
     * recommended
     */

    // avengers.component.ts
    export class AvengersComponent { }
    ```

### Service Names

  - Use consistent names for all services named after their feature. Use UpperCamelCase for services. Only suffix service and factories with `Service` when it is not clear what they are (i.e. when they are nouns).

### Directive Component Names

  - Use consistent names for all directives using camel-case. Use a short prefix to describe the area that the directives belong (some example are company prefix or project prefix).

## TSLint

Use the rules defined in the [tslint.json](tslint.json) file in order to follow the code conventions for Systelab

Remember to enable tslint in the project Settings (Language & Frameworks | Typescript | TSLint)

## Webstorm Code Style Scheme

Goto:

- File | Settings | Editor | Code Style for Windows and Linux
- WebStorm | Preferences | Editor | Code Style for macOS

Use the [following scheme](webstorm_ts_code_style.xml) for Webstorm Code Style Scheme.

```xml
<code_scheme name="Modulab CodeStyle TS copy" version="173">
  <option name="RIGHT_MARGIN" value="180" />
  <JSCodeStyleSettings>
    <option name="ALIGN_OBJECT_PROPERTIES" value="1" />
    <option name="ALIGN_VAR_STATEMENTS" value="1" />
    <option name="SPACE_BEFORE_FUNCTION_LEFT_PARENTH" value="false" />
  </JSCodeStyleSettings>
  <TypeScriptCodeStyleSettings>
    <option name="ALIGN_OBJECT_PROPERTIES" value="1" />
    <option name="ALIGN_VAR_STATEMENTS" value="1" />
    <option name="SPACE_BEFORE_FUNCTION_LEFT_PARENTH" value="false" />
    <option name="USE_PUBLIC_MODIFIER" value="true" />
    <option name="USE_DOUBLE_QUOTES" value="false" />
    <option name="IMPORTS_WRAP" value="0" />
    <option name="SPACES_WITHIN_IMPORTS" value="true" />
  </TypeScriptCodeStyleSettings>
  <codeStyleSettings language="JavaScript">
    <option name="KEEP_FIRST_COLUMN_COMMENT" value="false" />
    <option name="KEEP_BLANK_LINES_IN_CODE" value="1" />
    <option name="METHOD_CALL_CHAIN_WRAP" value="2" />
    <option name="DOWHILE_BRACE_FORCE" value="3" />
    <option name="WHILE_BRACE_FORCE" value="3" />
    <option name="FOR_BRACE_FORCE" value="3" />
    <indentOptions>
      <option name="USE_TAB_CHARACTER" value="true" />
    </indentOptions>
  </codeStyleSettings>
  <codeStyleSettings language="TypeScript">
    <option name="KEEP_FIRST_COLUMN_COMMENT" value="false" />
    <option name="KEEP_BLANK_LINES_IN_CODE" value="1" />
    <option name="ALIGN_MULTILINE_EXTENDS_LIST" value="true" />
    <option name="METHOD_CALL_CHAIN_WRAP" value="2" />
    <option name="IF_BRACE_FORCE" value="3" />
    <option name="DOWHILE_BRACE_FORCE" value="3" />
    <option name="WHILE_BRACE_FORCE" value="3" />
    <option name="FOR_BRACE_FORCE" value="3" />
    <indentOptions>
      <option name="USE_TAB_CHARACTER" value="true" />
    </indentOptions>
  </codeStyleSettings>
</code_scheme>

```
