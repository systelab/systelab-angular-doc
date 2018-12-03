# Code Conventions

The purpose of this style guide is to provide guidance on building Angular applications while standarizing some conventions that we have decided to use. Generally speaking you are not going to find anything different that what it is specified in the [Angular Style Guide](https://angular.io/guide/styleguide) by John Papa.

## Index

1. [Files](#files)
2. [Typescript](#typescript)
3. [Modules](#modules)
4. [Components](#components)
5. [Services](#services)
6. [Data Services](#data-services)
7. [Directives](#directives)
8. [Pipes](#pipes)
9. [TSLint](#tslint)
10. [Webstorm Code Style Scheme](#webstorm-code-style-scheme)

## Files

### Rule of One
  - Do define one thing, such as a service or component, per file.
  - Consider limiting files to 400 lines of code.
  - Consider limiting html files to 100 lines of code.

### File names
  - Use consistent names for all files following a pattern that describes the component's feature then (optionally) its type. Recommended pattern is `feature.type.ts`. 
  - Do use dots to separate the descriptive name from the type.
  - Do use dashed-case or kebab-case for feature names.
  - Do use conventional type names including .component, .service, .pipe, .module, and .directive. Invent additional type names if you must but take care not to create too many (It is optional to use .model).
  - Add the suffix -dialog for the modal components (`qc-chart-dialog.component.ts`)
  - Add the suffix -grid -combobox -listbox for the grid, combobox and listbox components (`doctor-grid.component.ts`, `doctor-combobox.component.ts`, `doctor-listbox.component.ts`)
  - For components, use the same component file name for templates and styles (but with a different extension). For example for `qc-chart.component.ts` use `qc-chart.component.html` and `qc-chart.component.scss`

### Unit test file names
  - Do name test specification files the same as the component they test.
  - Do name test specification files with a suffix of .spec.
  
### End-to-End (E2E) test file names
  - Do name end-to-end test specification files after the feature they test with a suffix of .e2e-spec.
  
### Folders names
  - Create folders named for the feature they represent. 
  - Do use dashed-case or kebab-case for feauture names.
  - When a folder grows to contain more than 7 files, start to consider creating a folder for them. Your threshold may be different, so adjust as needed.

## Typescript
  - Have a consistent set of coding, naming, and whitespace conventions.

### Classes
  - Do use upper camel case when naming classes.

### Constants
  - Do declare variables with const if their values should not change during the application lifetime.
  - Consider spelling const variables in lower camel case.
  - Do tolerate existing const variables that are spelled in UPPER_SNAKE_CASE.

### Interfaces
  - Do name an interface using upper camel case.
  - Consider naming an interface without an I prefix.
  - Consider using a class instead of an interface for services and declarables (components, directives, and pipes).
  - Consider using an interface for data models.

### Properties and methods
  - Do use lower camel case to name properties and methods.
  - Avoid prefixing private properties and methods with an underscore.
  - Do define small functions
  - Consider limiting methods to no more than 75 lines.

### Import line spacing
  - Consider leaving one empty line between third party imports and application imports.
  - Consider listing import lines alphabetized by the module.
  - Consider listing destructured imported symbols alphabetically.

## Modules

### Module names
  - Do append the symbol name with the suffix Module.
  - Do give the file name the .module.ts extension.
  - Do name the module after the feature and folder it resides in.
  - Do suffix a RoutingModule class name with RoutingModule.
  - Do end the filename of a RoutingModule with -routing.module.ts.

### Example

```typescript
@NgModule({
	imports:         [
		BrowserModule,
		FormsModule,
		DragDropModule,
		HttpClientModule,
		SystelabTranslateModule.forRoot(),
		SystelabPreferencesModule.forRoot(),
		SystelabComponentsModule.forRoot(),
		SystelabLoginModule.forRoot(),
		AgGridModule.withComponents([
			GridContextMenuCellRendererComponent,
			GridHeaderContextMenuComponent
		]),
		AppRoutingModule
	],
	declarations:    [
		PatientMaintenanceDialog,
		AppComponent,
		MainComponent,
		PageNotFoundComponent,
		LoginComponent
	],
	providers:       [
		{provide: BASE_PATH, useValue: environment.API_BASE_PATH},
		{provide: HTTP_INTERCEPTORS, useClass: EmptyBodyInterceptor, multi: true},
		MessagePopupService,
		DialogService
	],
	entryComponents: [
		PatientMaintenanceDialog
	],
	bootstrap:       [AppComponent]
})
export class AppModule {
}

```

## Components

### Component names
  - Do use consistent names for all assets named after what they represent.
  - Do match the name of the symbol to the name of the file.
  - Do use upper camel case for class names (`QualityControlComponent`)
  - Do append the symbol name with the conventional suffix (such as Component, Directive, Module, Pipe, or Service) for a thing of that type.
  - Add the suffix Dialog for the modal components (`DoctorDialog`)
  - Add the suffix Grid, Combobox or Listbox for the grid, combobox or listbox components (`DoctorGrid`, `DoctorComboBox`, `DoctorListBox`)
  
### Components as elements
  - Consider giving components an element selector, as opposed to attribute or class selectors.

### Extract templates and styles to their own files
  - Do extract templates and styles into a separate file, when more than 3 lines.
  - Do name the template file [component-name].component.html, where [component-name] is the component name.
  - Do name the style file [component-name].component.css, where [component-name] is the component name.
  - Do specify component-relative URLs, prefixed with ./.
  
### Component selectors
  - Do use dashed-case or kebab-case for naming the element selectors of components.

### Decorate input and output properties
  - Do use the @Input() and @Output() class decorators instead of the inputs and outputs properties of the @Directive and @Component metadata:
  - Consider placing @Input() or @Output() on the same line as the property it decorates.
  - Avoid input and output aliases except when it serves an important purpose.
  - Add member-access to all the properties, in that case use public

### Don't prefix output properties
  - Do name events without the prefix on.
  - Do name event handler methods with the prefix on followed by the event name.

### Member sequence
  - Do place properties up top followed by methods.

### Delegate complex component logic to services
  - Do limit logic in a component to only that required for the view. All other logic should be delegated to services.
  - Do move reusable logic to services and keep components simple and focused on their intended purpose.

### Put presentation logic in the component class
  - Do put presentation logic in the component class, and not in the template. Avoid the use of formulas,... in the template.

### Example 

```typescript
@Component({
	selector: 'systelab-calendar-footer',
	templateUrl: 'calendar-footer.component.html',
	styleUrls: ['calendar-footer.component.scss']
})
export class CalendarFooterComponent {

	@Input() public currentDate: Date;
	@Output() public clearDate: EventEmitter<void> = new EventEmitter<void>();

	constructor(private i18nService: I18nService) {
	}

	public onClearDate(): void {
		this.clearDate.emit();
	}
}
```

## Services

### Service names
  - Do use consistent names for all services named after their feature.
  - Do suffix a service class name with Service. For example DoctorService.

### Services are singletons
  - Do use services as singletons within the same injector. Use them for sharing data and functionality.

### Single responsibility
  - Do create services with a single responsibility that is encapsulated by its context.
  - Do create a new service once the service begins to exceed that singular purpose.

### Providing a service
  - Do provide a service with the app root injector in the @Injectable decorator of the service.

### Use the @Injectable() class decorator
  - Do use the @Injectable() class decorator instead of the @Inject parameter decorator when using types as tokens for the dependencies of a service.

### Example 

```typescript
@Injectable({
	providedIn: 'root'
})
export class LoadingService {

	protected loadingList: boolean[] = [];

	public setLoading() {
		this.loadingList.push(true);
	}

	public removeLoading() {
		if (this.loadingList.length > 0) {
			this.loadingList.pop();
		}
	}

	public isLoading(): boolean {
		return this.loadingList.length > 0;
	}
}
```

## Data Services
### Talk to the server through a service
  - If possible, do use Swagger Codegen
  - Do refactor logic for making data operations and interacting with data to a service.
  - Do make data services responsible for XHR calls, local storage, stashing in memory, or any other data operations.
  - A data service encapsulates these details. It's easier to evolve these details inside the service without affecting its consumers. And it's easier to test the consumers with mock service implementations.

### Example 

```typescript
@Injectable({
	providedIn: 'root'
})
export class PatientService extends BaseService {

	constructor(protected httpClient: HttpClient, protected apiGlobalsService: ApiGlobalsService,
	            @Optional() @Inject(BASE_PATH) basePath: string) {
		super(basePath, apiGlobalsService);
	}

	public createPatient(body: Patient): Observable<Patient> {
		if (body === null || body === undefined) {
			throw new Error('Required parameter body was null or undefined when calling createPatient.');
		}
		return this.httpClient.post<any>(`${this.basePath}/patients/patient`, body, {
			headers: this.getAuthorizationHeader(),
		});
	}
}
```

## Directives

### Directive names
  - Do use attribute directives when you have presentation logic without a template.
  - Do append the symbol name with the suffix Directive.
  - Do give the file name the .directive.ts extension.

### Directive selectors
  - Do Use lower camel case for naming the selectors of directives.
  - Do use a custom prefix for the selector of directives.
  - Do spell non-element selectors in lower camel case unless the selector is meant to match a native HTML attribute.

## Pipes

### Pipe names
  - Do use consistent names for all pipes, named after their feature.
  - Do append the symbol name with the suffix Pipe.
  - Do give the file name the .pipe.ts extension.

### Pipe selectors
  - Do Use lower camel case for naming the selectors of pipes.
  - Do use a custom prefix for the selector of pipes.

### Example
```typescript
@Pipe({
	name: 'datafilter'
})

export class DataFilterPipe implements PipeTransform {

	public transform(input: any[], searchString: string): any {
		const result = [];
		if (!searchString) {
			return input;
		}

		for (const element of input) {
			if (element.displayName.toLowerCase()
					.indexOf(searchString.toLowerCase()) > -1) {
				result.push(element);
			}
		}
		return result;
	}
}

```

## TSLint

Use the rules defined in the [tslint.json](tslint.json) file in order to follow the code conventions for Systelab

Remember to enable tslint in the project Settings (Language & Frameworks | Typescript | TSLint)

## Webstorm Code Style Scheme

Goto:

- File | Settings | Editor | Code Style for Windows and Linux
- WebStorm | Preferences | Editor | Code Style for macOS

Use the [following scheme](webstorm_ts_code_style.xml) for Webstorm Code Style Scheme.

```xml
<code_scheme name="Systelab CodeStyle TS" version="173">
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
