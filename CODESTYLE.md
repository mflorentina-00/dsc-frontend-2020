# Development Guide

### Vocabulary

Each guideline describes either a good or bad practice, and all have a consistent presentation.

The wording of each guideline indicates how strong the recommendation is.

**Do** is one that should always be followed. _Always_ might be a bit too strong of a word. Guidelines that literally should always be followed are extremely rare. On the other hand, you need a really unusual case for breaking a Do guideline.

**Consider** guidelines should generally be followed. If you fully understand the meaning behind the guideline and have a good reason to deviate, then do so. Please strive to be consistent.

**Avoid** indicates something you should almost never do. Code examples to avoid have an unmistakable red header.

**Why?** gives reasons for following the previous recommendations.

## Angular - [From Angular Style Guide](https://angular.io/guide/styleguide)

### File structure conventions

Some code examples display a file that has one or more similarly named companion files. For example, _component-name.component.ts_ and _component-name.component.html_.

The guideline uses the shortcut _component-name.component.ts|html|css|spec_ to represent those various files. Using this shortcut makes this guide's file structures easier to read and more terse.

### Single responsibility

Apply the [single responsibility principle (SRP)](https://wikipedia.org/wiki/Single_responsibility_principle) to all components, services, and other symbols. This helps make the app cleaner, easier to read and maintain, and more testable.

#### Rule of One

_Angular 01-01_

**Do** define one thing, such as a service or component, per file.

**Consider** limiting files to 400 lines of code.

**Why?** One component per file makes it far easier to read, maintain, and avoid collisions with teams in source control.

**Why?** One component per file avoids hidden bugs that often arise when combining components in a file where they may share variables, create unwanted closures, or unwanted coupling with dependencies.

**Why?** A single component can be the default export for its file which facilitates lazy loading with the router.

The key is to make the code more reusable, easier to read, and less mistake prone.

#### Small functions

_Angular 01-02_

**Do** define small functions

**Consider** limiting to no more than 75 lines.

**Why?** Small functions are easier to test, especially when they do one thing and serve one purpose.

**Why?** Small functions promote reuse.

**Why?** Small functions are easier to read.

**Why?** Small functions are easier to maintain.

**Why?** Small functions help avoid hidden bugs that come with large functions that share variables with external scope, create unwanted closures, or unwanted coupling with dependencies.


### Naming

Naming conventions are hugely important to maintainability and readability. This guide recommends naming conventions for the file name and the symbol name.

#### General Naming Guidelines

_Angular 02-01_

**Do** use consistent names for all symbols.

**Do** follow a pattern that describes the symbol's feature then its type. The recommended pattern is **feature-name.type.ts**.

**Why?** Naming conventions help provide a consistent way to find content at a glance. Consistency within the project is vital. Consistency with a team is important. Consistency across a company provides tremendous efficiency.

**Why?** The naming conventions should simply help find desired code faster and make it easier to understand.

**Why?** Names of folders and files should clearly convey their intent.

#### Separate file names with dots and dashes

_Angular 02-02_

**Do** use dashes to separate words in the descriptive name.

**Do** use dots to separate the descriptive name from the type.

**Do** use consistent type names for all components following a pattern that describes the component's feature then its type. A recommended pattern is feature.type.ts.

**Do** use conventional type names including .service, .component, .pipe, .module, and .directive. Invent additional type names if you must but take care not to create too many.

**Why?** Type names provide a consistent way to quickly identify what is in the file.

**Why?** Type names make it easy to find a specific file type using an editor or IDE's fuzzy search techniques.

**Why?** Unabbreviated type names such as .service are descriptive and unambiguous. Abbreviations such as .srv, .svc, and .serv can be confusing.

**Why?** Type names provide pattern matching for any automated tasks.

#### Symbols and file names

_Angular 02-03_

**Do** use consistent names for all assets named after what they represent.

**Do** use upper camel case for class names.

**Do** match the name of the symbol to the name of the file.

**Do** append the symbol name with the conventional suffix (such as Component, Directive, Module, Pipe, or Service) for a thing of that type.

**Do** give the filename the conventional suffix (such as .component.ts, .directive.ts, .module.ts, .pipe.ts, or .service.ts) for a file of that type.

**Why?** Consistent conventions make it easy to quickly identify and reference assets of different types.

| Symbol Name |	File Name |
|---|---|
| export class AppComponent { } | app.component.ts |
| export class HeroesComponent { } | heroes.component.ts |
| export class HeroListComponent { } | hero-list.component.ts |
| export class HeroDetailComponent { } | hero-detail.component.ts |
| export class ValidationDirective { } | validation.directive.ts |
| export class AppModule | app.module.ts |
| export class InitCapsPipe implements PipeTransform { } | init-caps.pipe.ts |
| export class UserProfileService { } | user-profile.service.ts |

#### Service names

_Angular 02-04_

**Do** use consistent names for all services named after their feature.

**Do** suffix a service class name with Service. For example, something that gets data or heroes should be called a DataService or a HeroService.

A few terms are unambiguously services. They typically indicate agency by ending in "-er". You may prefer to name a service that logs messages Logger rather than LoggerService. Decide if this exception is agreeable in your project. As always, strive for consistency.

**Why?** Provides a consistent way to quickly identify and reference services.

**Why?** Clear service names such as Logger do not require a suffix.

**Why?** Service names such as Credit are nouns and require a suffix and should be named with a suffix when it is not obvious if it is a service or something else.

| Symbol Name |	File Name |
|---|---|
| export class HeroDataService { } | hero-data.service.ts |
| export class CreditService { } | credit.service.ts |
| export class Logger { } | logger.service.ts |

#### Component selectors

_Angular 02-05_

**Do** use dashed-case or kebab-case for naming the element selectors of components.

**Why?** Keeps the element names consistent with the specification for Custom Elements.

`hero-button.component.ts`

    /* avoid */

    @Component({
      selector: 'tohHeroButton',
      templateUrl: './hero-button.component.html'
    })
    export class HeroButtonComponent {}

    /* do */

    @Component({
      selector: 'toh-hero-button',
      templateUrl: './hero-button.component.html'
    })
    export class HeroButtonComponent {}

#### Component custom prefix

_Angular 02-06_

**Do** use a hyphenated, lowercase element selector value; for example, admin-users.

**Do** use a custom prefix for a component selector. For example, the prefix toh represents Tour of Heroes and the prefix admin represents an admin feature area.

**Do** use a prefix that identifies the feature area or the app itself.

**Why?** Prevents element name collisions with components in other apps and with native HTML elements.

**Why?** Makes it easier to promote and share the component in other apps.

**Why?** Components are easy to identify in the DOM.

`hero.component.ts`

    /* avoid */

    // HeroComponent is in the Tour of Heroes feature
    @Component({
      selector: 'hero'
    })
    export class HeroComponent {}

    /* do */

    @Component({
      selector: 'toh-hero'
    })
    export class HeroComponent {}


#### Directive selectors

_Angular 02-07_

**Do** Use lower camel case for naming the selectors of directives.

**Why?** Keeps the names of the properties defined in the directives that are bound to the view consistent with the attribute names.

**Why?** The Angular HTML parser is case sensitive and recognizes lower camel case.

#### Directive custom prefix

_Angular 02-08_

**Do** use a custom prefix for the selector of directives (e.g, the prefix toh from Tour of Heroes).

**Do** spell non-element selectors in lower camel case unless the selector is meant to match a native HTML attribute.

**Why?** Prevents name collisions.

**Why?** Directives are easily identified.

`validate.directive.ts`

    /* avoid */

    @Directive({
      selector: '[validate]'
    })
    export class ValidateDirective {}

    /* do */

    @Directive({
      selector: '[tohValidate]'
    })
    export class ValidateDirective {}

#### Pipe names

_Angular 02-09_

**Do** use consistent names for all pipes, named after their feature. The pipe class name should use UpperCamelCase (the general convention for class names), and the corresponding name string should use lowerCamelCase. The name string cannot use hyphens ("dash-case" or "kebab-case").

**Why?** Provides a consistent way to quickly identify and reference pipes.

#### Unit test file names

_Angular 02-10_

**Do** name test specification files the same as the component they test.

**Do** name test specification files with a suffix of .spec.

**Why?** Provides a consistent way to quickly identify tests.

**Why?** Provides pattern matching for jest or other test runners.

| Test Type	| File Names |
|---|---|
| Components | heroes.component.spec.ts |
| Services | logger.service.spec.ts |
| Pipes | ellipsis.pipe.spec.ts |

#### Angular NgModule names

_Angular 02-11_

**Do** append the symbol name with the suffix Module.

**Do** give the file name the .module.ts extension.

**Do** name the module after the feature and folder it resides in.

**Why?** Provides a consistent way to quickly identify and reference modules.

**Why?** Upper camel case is conventional for identifying objects that can be instantiated using a constructor.

**Why?** Easily identifies the module as the root of the same named feature.

**Do** suffix a RoutingModule class name with RoutingModule.

**Do** end the filename of a RoutingModule with -routing.module.ts.

**Why?** A RoutingModule is a module dedicated exclusively to configuring the Angular router. A consistent class and file name convention make these modules easy to spot and verify.

| Symbol Name | File Name |
|---|---|
| export class AppModule { } | app.module.ts |
| export class HeroesModule { } | heroes.module.ts |
| export class VillainsModule { } | villains.module.ts |
| export class AppRoutingModule { } | app-routing.module.ts |
| export class HeroesRoutingModule { } | heroes-routing.module.ts |

### Application structure and NgModules

#### LIFT

_Angular 03-01_

**Do** structure the app such that you can Locate code quickly, Identify the code at a glance, keep the Flattest structure you can, and Try to be DRY.

**Do** define the structure to follow these four basic guidelines, listed in order of importance.

**Why?** LIFT provides a consistent structure that scales well, is modular, and makes it easier to increase developer efficiency by finding code quickly. To confirm your intuition about a particular structure, ask: can I quickly open and start work in all of the related files for this feature?

##### Locate

_Angular 03-02_

**Do** make locating code intuitive, simple, and fast.

**Why?** To work efficiently you must be able to find files quickly, especially when you do not know (or do not remember) the file names. Keeping related files near each other in an intuitive location saves time. A descriptive folder structure makes a world of difference to you and the people who come after you.

##### Identify

_Angular 03-03_

**Do** name the file such that you instantly know what it contains and represents.

**Do** be descriptive with file names and keep the contents of the file to exactly one component.

**Avoid** files with multiple components, multiple services, or a mixture.

**Why?** Spend less time hunting and pecking for code, and become more efficient. Longer file names are far better than short-but-obscure abbreviated names.

##### Flat

_Angular 03-04_

**Do** keep a flat folder structure as long as possible.

**Consider** creating sub-folders when a folder reaches seven or more files.

**Consider** configuring the IDE to hide distracting, irrelevant files such as generated .js and .js.map files.

**Why?** No one wants to search for a file through seven levels of folders. A flat structure is easy to scan.

##### T-DRY (Try to be DRY)

_Angular 03-05_

**Do** be DRY (Don't Repeat Yourself).

**Avoid** being so DRY that you sacrifice readability.

**Why?** Being DRY is important, but not crucial if it sacrifices the other elements of LIFT. That's why it's called T-DRY. For example, it's redundant to name a template hero-view.component.html because with the .html extension, it is obviously a view. But if something is not obvious or departs from a convention, then spell it out.

#### Overall structural guidelines

_Angular 03-06_

**Do** start small but keep in mind where the app is heading down the road.

**Do** have a near term view of implementation and a long term vision.

**Do** put all of the app's code in a folder named _src_.

**Consider** creating a folder for a component when it has multiple accompanying files (.ts, .html, .css and .spec).

**Why?** Helps keep the app structure small and easy to maintain in the early stages, while being easy to evolve as the app grows.

**Why?** Components often have four files (e.g. *.html, *.css, *.ts, and *.spec.ts) and can clutter a folder quickly.

#### Folders-by-feature structure

_Angular 03-07_

**Do** create folders named for the feature area they represent.

**Why?** A developer can locate the code and identify what each file represents at a glance. The structure is as flat as it can be and there are no repetitive or redundant names.

**Why?** The LIFT guidelines are all covered.

**Why?** Helps reduce the app from becoming cluttered through organizing the content and keeping them aligned with the LIFT guidelines.

**Why?** When there are a lot of files, for example 10+, locating them is easier with a consistent folder structure and more difficult in a flat structure.

**Do** create an NgModule for each feature area.

**Why?** NgModules make it easy to lazy load routable features.

**Why?** NgModules make it easier to isolate, test, and reuse features.

#### Feature modules

_Angular 03-08_

**Do** create an NgModule for all distinct features in an application; for example, a Heroes feature.

**Do** place the feature module in the same named folder as the feature area; for example, in app/heroes.

**Do** name the feature module file reflecting the name of the feature area and folder; for example, app/heroes/heroes.module.ts.

**Do** name the feature module symbol reflecting the name of the feature area, folder, and file; for example, app/heroes/heroes.module.ts defines HeroesModule.

**Why?** A feature module can expose or hide its implementation from other modules.

**Why?** A feature module identifies distinct sets of related components that comprise the feature area.

**Why?** A feature module can easily be routed to both eagerly and lazily.

**Why?** A feature module defines clear boundaries between specific functionality and other application features.

**Why?** A feature module helps clarify and make it easier to assign development responsibilities to different teams.

**Why?** A feature module can easily be isolated for testing.

#### Shared feature module

_Angular 03-09_

**Do** create a feature module named SharedModule in a shared folder; for example, app/shared/shared.module.ts defines SharedModule.

**Do** declare components, directives, and pipes in a shared module when those items will be re-used and referenced by the components declared in other feature modules.

**Consider** using the name SharedModule when the contents of a shared module are referenced across the entire application.

**Consider** not providing services in shared modules. Services are usually singletons that are provided once for the entire application or in a particular feature module. There are exceptions, however. For example, in the sample code that follows, notice that the SharedModule provides FilterTextService. This is acceptable here because the service is stateless;that is, the consumers of the service aren't impacted by new instances.

**Do** import all modules required by the assets in the SharedModule; for example, CommonModule and FormsModule.

**Why?** SharedModule will contain components, directives and pipes that may need features from another common module; for example, ngFor in CommonModule.

**Do** declare all components, directives, and pipes in the SharedModule.

**Do** export all symbols from the SharedModule that other feature modules need to use.

**Why?** SharedModule exists to make commonly used components, directives and pipes available for use in the templates of components in many other modules.

**Avoid** specifying app-wide singleton providers in a SharedModule. Intentional singletons are OK. Take care.

**Why?** A lazy loaded feature module that imports that shared module will make its own copy of the service and likely have undesirable results.

**Why?** You don't want each module to have its own separate instance of singleton services. Yet there is a real danger of that happening if the SharedModule provides a service.

#### Lazy Loaded folders

_Angular 03-10_

A distinct application feature or workflow may be lazy loaded or loaded on demand rather than when the application starts.

**Do** put the contents of lazy loaded features in a lazy loaded folder. A typical lazy loaded folder contains a routing component, its child components, and their related assets and modules.

**Why?** The folder makes it easy to identify and isolate the feature content.

#### Never directly import lazy loaded folders

_Angular 03-11_

**Avoid** allowing modules in sibling and parent folders to directly import a module in a lazy loaded feature.

**Why?** Directly importing and using a module will load it immediately when the intention is to load it on demand.

### Components

#### Components as elements

_Angular 04-01_

**Consider** giving components an element selector, as opposed to attribute or class selectors.

**Why?** Components have templates containing HTML and optional Angular template syntax. They display content. Developers place components on the page as they would native HTML elements and web components.

**Why?** It is easier to recognize that a symbol is a component by looking at the template's html.

#### Extract templates and styles to their own files

_Angular 04-02_

**Do** extract templates and styles into a separate file, when more than 3 lines.

**Do** name the template file [component-name].component.html, where [component-name] is the component name.

**Do** name the style file [component-name].component.css, where [component-name] is the component name.

**Do** specify component-relative URLs, prefixed with ./.

**Why?** Large, inline templates and styles obscure the component's purpose and implementation, reducing readability and maintainability.

**Why?** In most editors, syntax hints and code snippets aren't available when developing inline templates and styles. The Angular TypeScript Language Service (forthcoming) promises to overcome this deficiency for HTML templates in those editors that support it; it won't help with CSS styles.

**Why?** A component relative URL requires no change when you move the component files, as long as the files stay together.

**Why?** The ./ prefix is standard syntax for relative URLs; don't depend on Angular's current ability to do without that prefix.

#### Decorate input and output properties

_Angular 04-03_

**Do** use the _@Input()_ and _@Output()_ class decorators instead of the inputs and outputs properties of the @Directive and @Component metadata:

**Consider** placing @Input() or @Output() on the same line as the property it decorates.

**Why?** It is easier and more readable to identify which properties in a class are inputs or outputs.

**Why?** If you ever need to rename the property or event name associated with @Input or @Output, you can modify it in a single place.

**Why?** The metadata declaration attached to the directive is shorter and thus more readable.

**Why?** Placing the decorator on the same line usually makes for shorter code and still easily identifies the property as an input or output. Put it on the line above when doing so is clearly more readable.

#### Avoid aliasing inputs and outputs

_Angular 04-04_

**Avoid** input and output aliases except when it serves an important purpose.

**Why?** Two names for the same property (one private, one public) is inherently confusing.

**Why?** You should use an alias when the directive name is also an input property, and the directive name doesn't describe the property.

`hero-button.component.ts`

    /* avoid pointless aliasing */

    @Component({
      selector: 'toh-hero-button',
      template: `<button>{{label}}</button>`
    })
    export class HeroButtonComponent {
      // Pointless aliases
      @Output('changeEvent') change = new EventEmitter<any>();
      @Input('labelAttribute') label: string;
    }

`app.component.html`

    <!-- avoid -->

    <toh-hero-button labelAttribute="OK" (changeEvent)="doSomething()">
    </toh-hero-button>

`hero-button.component.ts`

    <!-- do -->

    @Component({
      selector: 'toh-hero-button',
      template: `<button>{{label}}</button>`
    })
    export class HeroButtonComponent {
      // No aliases
      @Output() change = new EventEmitter<any>();
      @Input() label: string;
    }

`app.component.html`

    <!-- do -->

    <toh-hero-button label="OK" (change)="doSomething()">
    </toh-hero-button>

#### Member sequence

_Angular 04-05_

**Do** place properties up top followed by methods.

**Do** place private members after public members, alphabetized.

**Why?** Placing members in a consistent sequence makes it easy to read and helps instantly identify which members of the component serve which purpose.

#### Delegate complex component logic to services

_Angular 04-06_

**Do** limit logic in a component to only that required for the view. All other logic should be delegated to services.

**Do** move reusable logic to services and keep components simple and focused on their intended purpose.

**Why?** Logic may be reused by multiple components when placed within a service and exposed via a function.

**Why?** Logic in a service can more easily be isolated in a unit test, while the calling logic in the component can be easily mocked.

**Why?** Removes dependencies and hides implementation details from the component.

**Why?** Keeps the component slim, trim, and focused.

#### Don't prefix output properties

_Angular 04-07_

**Do** name events without the prefix on.

**Do** name event handler methods with the prefix on followed by the event name.

**Why?** This is consistent with built-in events such as button clicks.

**Why?** Angular allows for an alternative syntax on-*. If the event itself was prefixed with on this would result in an on-onEvent binding expression.

`hero.component.ts`

    /* avoid */

    export class HeroComponent {
      @Output() onSavedTheDay = new EventEmitter<boolean>();
    }

`app.component.html`

    <!-- avoid -->

    <toh-hero (onSavedTheDay)="onSavedTheDay($event)"></toh-hero>

`hero.component.ts`

    <!-- do -->

    export class HeroComponent {
      @Output() savedTheDay = new EventEmitter<boolean>();
    }

`app.component.html`

    <!-- do -->

    <toh-hero (savedTheDay)="onSavedTheDay($event)"></toh-hero>

#### Put presentation logic in the component class

_Angular 04-08_

**Do** put presentation logic in the component class, and not in the template.

**Why?** Logic will be contained in one place (the component class) instead of being spread in two places.

**Why?** Keeping the component's presentation logic in the class instead of the template improves testability, maintainability, and reusability.

    /* avoid */

    @Component({
      selector: 'toh-hero-list',
      template: `
        <section>
          Our list of heroes:
          <hero-profile *ngFor="let hero of heroes" [hero]="hero">
          </hero-profile>
          Total powers: {{totalPowers}}<br>
          Average power: {{totalPowers / heroes.length}}
        </section>
      `
    })
    export class HeroListComponent {
      heroes: Hero[];
      totalPowers: number;
    }

    /* do */

    @Component({
      selector: 'toh-hero-list',
      template: `
        <section>
          Our list of heroes:
          <toh-hero *ngFor="let hero of heroes" [hero]="hero">
          </toh-hero>
          Total powers: {{totalPowers}}<br>
          Average power: {{avgPower}}
        </section>
      `
    })
    export class HeroListComponent {
      heroes: Hero[];
      totalPowers: number;

      public get avgPower() {
        return this.totalPowers / this.heroes.length;
      }
    }

### Directives

#### Use directives to enhance an element

_Angular 05-01_

**Do** use attribute directives when you have presentation logic without a template.

**Why?** Attribute directives don't have an associated template.

**Why?** An element may have more than one attribute directive applied.

### Services

#### Services are singletons

_Angular 06-01_

**Do** use services as singletons within the same injector. Use them for sharing data and functionality.

**Why?** Services are ideal for sharing methods across a feature area or an app.

**Why?** Services are ideal for sharing stateful in-memory data.

#### Single responsibility

_Angular 06-02_

**Do** create services with a single responsibility that is encapsulated by its context.

**Do** create a new service once the service begins to exceed that singular purpose.

**Why?** When a service has multiple responsibilities, it becomes difficult to test.

**Why?** When a service has multiple responsibilities, every component or service that injects it now carries the weight of them all.

#### Providing a service

_Angular 06-03_

**Do** provide a service with the app root injector in the @Injectable decorator of the service.

**Why?** The Angular injector is hierarchical.

**Why?** When you provide the service to a root injector, that instance of the service is shared and available in every class that needs the service. This is ideal when a service is sharing methods or state.

**Why?** When you register a service in the @Injectable decorator of the service, optimization tools such as those used by the Angular CLI's production builds can perform tree shaking and remove services that aren't used by your app.

**Why?** This is not ideal when two different components need different instances of a service. In this scenario it would be better to provide the service at the component level that needs the new and separate instance.

    /* avoid */

    export class HeroArena {
      constructor(
          @Inject(HeroService) private heroService: HeroService,
          @Inject(HttpClient) private http: HttpClient) {}
    }

    /* do */

    @Injectable()
    export class HeroArena {
      constructor(
        private heroService: HeroService,
        private http: HttpClient,
      ) {}
    }

### Lifecycle hooks

Use Lifecycle hooks to tap into important events exposed by Angular.

#### Implement lifecycle hook interfaces

_Angular 07-01_

**Do** implement the lifecycle hook interfaces.

**Why?** Lifecycle interfaces prescribe typed method signatures. Use those signatures to flag spelling and syntax mistakes.
