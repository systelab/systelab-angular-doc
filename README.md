# Code Conventions

## Angular code conventions

The purpose of this style guide is to provide guidance on building Angular applications while standarizing some conventions that we have decided to use. Generally speaking you are not going to find anything different that what it is specified in the [Angular Style Guide](https://angular.io/guide/styleguide) by John Papa.

### Naming

#### Naming Guidelines

  - Use consistent names for all components following a pattern that describes the component's feature then (optionally) its type. Recommended pattern is `feature.type.ts`. There are 2 names for most assets:
    * the file name (`avengers.component.ts`)
    * the registered component name with Angular (`Component`)
  - Do use conventional type names including .service, .component, .pipe, .module, and .directive. Invent additional type names if you must but take care not to create too many.
  
#### Symbols and file names
  - Do use consistent names for all assets named after what they represent.
  - Do use upper camel case for class names.
  - Do match the name of the symbol to the name of the file.
  - Do append the symbol name with the conventional suffix (such as Component, Directive, Module, Pipe, or Service) for a thing of that type.
  - Do give the filename the conventional suffix (such as .component.ts, .directive.ts, .module.ts, .pipe.ts, or .service.ts) for a file of that type.

#### Service names
  - Do use consistent names for all services named after their feature.
  - Do suffix a service class name with Service. For example, something that gets data or heroes should be called a DataService or a HeroService.

#### Component selectors
  - Do use dashed-case or kebab-case for naming the element selectors of components.

#### Component custom prefix
  - Do use a hyphenated, lowercase element selector value (e.g. admin-users).
  - Do use a custom prefix for a component selector. For example, the prefix toh represents from Tour of Heroes and the prefix admin represents an admin feature area.
  - Do use a prefix that identifies the feature area or the app itself.

#### Directive selectors
  - Do Use lower camel case for naming the selectors of directives.

#### Directive custom prefix
  - Do use a custom prefix for the selector of directives (e.g, the prefix toh from Tour of Heroes).
  - Do spell non-element selectors in lower camel case unless the selector is meant to match a native HTML attribute.

#### Pipe names
  - Do use consistent names for all pipes, named after their feature.

#### Unit test file names
  - Do name test specification files the same as the component they test.
  - Do name test specification files with a suffix of .spec.
  
#### End-to-End (E2E) test file names
  - Do name end-to-end test specification files after the feature they test with a suffix of .e2e-spec.

#### Angular NgModule names
  - Do append the symbol name with the suffix Module.
  - Do give the file name the .module.ts extension.
  - Do name the module after the feature and folder it resides in.
  - Do suffix a RoutingModule class name with RoutingModule.
  - Do end the filename of a RoutingModule with -routing.module.ts.

### Components

#### Components as elements
  - Consider giving components an element selector, as opposed to attribute or class selectors.

#### Extract templates and styles to their own files
  - Do extract templates and styles into a separate file, when more than 3 lines.
  - Do name the template file [component-name].component.html, where [component-name] is the component name.
  - Do name the style file [component-name].component.css, where [component-name] is the component name.
  - Do specify component-relative URLs, prefixed with ./.

#### Decorate input and output properties
  - Do use the @Input() and @Output() class decorators instead of the inputs and outputs properties of the @Directive and @Component metadata:
  - Consider placing @Input() or @Output() on the same line as the property it decorates.
  - Avoid input and output aliases except when it serves an important purpose.

#### Don't prefix output properties
  - Do name events without the prefix on.
  - Do name event handler methods with the prefix on followed by the event name.

#### Member sequence
  - Do place properties up top followed by methods.

#### Delegate complex component logic to services
  - Do limit logic in a component to only that required for the view. All other logic should be delegated to services.
  - Do move reusable logic to services and keep components simple and focused on their intended purpose.

#### Put presentation logic in the component class
  - Do put presentation logic in the component class, and not in the template. Avoid the use of formulas,... in the template.

### Services
#### Services are singletons
  - Do use services as singletons within the same injector. Use them for sharing data and functionality.

#### Single responsibility
  - Do create services with a single responsibility that is encapsulated by its context.
  - Do create a new service once the service begins to exceed that singular purpose.

#### Providing a service
  - Do provide a service with the app root injector in the @Injectable decorator of the service.

#### Use the @Injectable() class decorator
  - Do use the @Injectable() class decorator instead of the @Inject parameter decorator when using types as tokens for the dependencies of a service.

### Data Services
#### Talk to the server through a service
  - Do refactor logic for making data operations and interacting with data to a service.
  - Do make data services responsible for XHR calls, local storage, stashing in memory, or any other data operations.
  - A data service encapsulates these details. It's easier to evolve these details inside the service without affecting its consumers. And it's easier to test the consumers with mock service implementations.

### Directives
#### Use directives to enhance an element
  - Do use attribute directives when you have presentation logic without a template.


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
