# .NET Angular Stack Snippets  

[GitHub](https://github.com/JaimeStill/dna-snippets)

## Contents

* [Overview](#overview)
* [Available Snippets](#available-snippets)
    * [.NET Snippets](#net-snippets)
    * [Angular Snippets](#angular-snippets)
* [Snippet Anatomy](#snippet-anatomy)
    * [.NET Snippet Anatomy](#net-snippet-anatomy)
    * [Angular Snippet Anatomy](#angular-snippet-anatomy)
        * [Angular Template Anatomy](#angular-template-anatomy)

## Overview  
[Back to Top](#contents)  

Snippets are called with the following convention: `dna.{snippet}`  

In this documentation, fillable snippet sections are identified using the same convention they are written with: `${i:default}`, where `i` is the tab-stop index, and `default` is the default value. I.e. - `${1:Project}`.

## Available Snippets  

### .NET Snippets
[Back to Top](#contents)  

Type | Name | FileType
-----|------|---------
Entity Class | `dna.ent-class` | C#
Extension Class | `dna.ext-class` | C#
Extension Method | `dna.ext-method` | C#
Extension Get Method | `dna.ext-get` | C#
Extension Entity Method | `dna.ext-entity` | C#
Extensions Validate Method | `dna.ext-validate` | C#
Extensions Validate Async Method | `dna.ext-validate-async` | C#
Middleware Class | `dna.mw-class` | C#
Middleware Extension | `dna.mw-extension` | C#
Controller Class | `dna.ctl-class` | C#
Controller Get Method | `dna.ctl-get` | C#
Controller Post Method | `dna.ctl-post` | C#
Controller Upload Method | `dna.ctl-upload` | C#
SignalR Hub Class | `dna.sgl-hub` | C#
SignalR Hub Trigger | `dna.sgl-trigger` | C#

### Angular Snippets
[Back to Top](#contents)  

Type | Name | FileType
-----|------|---------
Model Interface | `dna.model` | TypeScript
Service Class | `dna.service` | TypeScript
Service Http Function | `dna.http-func` | TypeScript
Service Http Promise | `dna.http-promise` | TypeScript
SignalR Service Class | `dna.sgl-service` | TypeScript
SignalR Trigger Function | `dna.sgl-trigger` | TypeScript
Component Class | `dna.component` | TypeScript
Pipe Class | `dna.pipe` | TypeScript
Route Class | `dna.route` | TypeScript
Dialog Class | `dna.dialog` | TypeScript
Observable Input | `dna.obs-input` | TypeScript
Component Index | `dna.idx-component` | TypeScript
Dialog Index | `dna.idx-dialog` | TypeScript
Model Index | `dna.idx-model` | TypeScript
Pipe Index | `dna.idx-pipe` | TypeScript
Route Index | `dna.idx-route` | TypeScript
Child Route Index | `dna.idx-child-route` | TypeScript
Service Index | `dna.idx-service` | TypeScript
Dialog Template | `dna.dialog` | HTML
Card Shell | `dna.card-shell` | HTML
Flex Container | `dna.flex-container` | HTML
Async Container | `dna.async-container` | HTML
Loading Template | `dna.loading-template` | HTML
Searchbar | `dna.searchbar` | HTML
Material Select | `dna.mat-select` | HTML
Material Input | `dna.mat-input` | HTML
Material Input Template Reference Variable | `dna.mat-input-trv` | HTML
Material Textarea | `dna.mat-textarea` | HTML
Material Slider | `dna.mat-slider` | HTML
Material Slide Toggle | `dna.mat-slide-toggle` | HTML
Material Menu | `dna.mat-menu` | HTML
Material Tab Nav | `dna.mat-tab-nav` | HTML

## Snippet Anatomy

### .NET Snippet Anatomy  
[Back to Top](#contents)  

**Entity Class**  

`dna.ent-class`  

Parameters:
* `Project` - Project namespace root
* `Entity` - Entity class name

```cs
using System;
using System.Collections.Generic;

namespace ${1:Project}.Data.Entities
{
    public class ${2:Entity}
    {
        public int Id { get; set; }
        
        // ENTRY POINT

        public DateTime CreatedDate { get; set; }
        public bool IsDeleted { get; set; }
    }
}
```

**Extension Class**  

`dna.ext-class`  

Parameters:
* `Project` - Project namespace root
* `Entity` - Extension class name

```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.EntityFrameworkCore;
using ${1:Project}.Data.Entities;

namespace ${1:Project}.Data.Extensions
{
    public static class ${2:Entity}Extensions
    {
        // ENTRY POINT
    }
}
```

**Extension Method**  

`dna.ext-method`  

Parameters:
* `Method` - Extension method name
* `T` - Extension method argument type
* `arg` - Extension method name


```cs
public static async Task ${1:Method}(this ${2:T} ${3:arg})
{
    // ENTRY POINT
}
```

**Extension Get Method**  

`dna.ext-get`  

Parameters:
* `T` - Extension method return type
* `Get` - Extension method name

```cs
public static async Task<${1:T}> ${2:Get}(this AppDbContext db)
{
    // ENTRY POINT
}
```

**Extension Entity Method**  

`dna.ext-entity`  

Parameters:
* `Method` - Extension method name
* `T` - Extension method argument type
* `arg` - Extension method argument name

```cs
public static async Task ${1:Method}(this AppDbContext db, ${2:T} ${3:arg})
{
    // ENTRY POINT
}
```

**Extension Validate Method**  

`dna.ext-validate`  

Parameters:
* `T` - Extension method argument type
* `arg` - Extension method argument name

```cs
public static bool Validate(this ${1:T} ${2:arg})
{
    // ENTRY POINT

    return true;
}
```  

**Extension Validate Async Method**  

`dna.ext-validate-async`  

Parameters:
* `T` - Extension method argument type
* `arg` - Extension method argument name

```cs
public static async Task<bool> Validate(this ${1:T} ${2:arg}, AppDbContext db)
{
    // ENTRY POINT

    return true;
}
```

**Middleware Class**  

`dna.mw-class`  

Parameters:
* `Namespace` - Namespace for this class
* `App` - Middleware class name

```cs
using System.Threading.Tasks;
using Microsoft.AspNetCore.Http;

namespace ${1:Namespace}
{
    public class ${2:App}Middleware
    {
        private readonly RequestDelegate next;

        public ${2:App}Middleware(RequestDelegate next)
        {
            this.next = next;
        }

        public async Task Invoke(HttpContext context)
        {
            // ENTRY POINT

            await next(context);
        }
    }
}
```

**Middleware Extension**  

`dna.mw-extension`  

Parameters:
* `Namespace` - Namespace containing middleware class
* `Middleware` - Extension class name
* `App` - Middleware class name

```cs
using ${1:Namespace};

namespace Microsoft.AspNetCore.Builder
{
    public static class ${2:Middleware}Extensions
    {
        public static IApplicationBuilder Use${3:App}Middleware(this IApplicationBuilder builder) =>
            builder.UseMiddleware<${3:App}Middleware>();
    }
}
```

**Controller Class**  

`dna.ctl-class`  

Parameters:
* `Project` - Project namespace name
* `Entity` - Controller name

```cs
using System.Collections.Generic;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc;
using ${1:Project}.Data;
using ${1:Project}.Data.Entities;
using ${1:Project}.Data.Extensions;

namespace ${1:Project}.Web.Controllers
{
    [Route("api/[controller]")]
    public class ${2:Entity}Controller : Controller
    {
        private AppDbContext db;

        public ${2:Entity}Controller(AppDbContext db)
        {
            this.db = db;
        }

        // ENTRY POINT
    }
}
```

**Controller Get Method**  

`dna.ctl-get`  

Parameters:
* `T` - Action method return type
* `Get` - Action method name

```cs
[HttpGet("[action]")]
public async Task<${1:T}> ${2:Get}() => await db.${2:Get}();
```

**Controller Post Method**  

`dna.ctl-post`  

Parameters:
* `Post` - Action method name
* `T` - Action method argument type
* `arg` - Action method argument name

```cs
[HttpPost("[action]")]
public async Task METHOD([FromBody]TYPE ARG) => await db.METHOD(ARG);
```

**Controller Upload Method**  

`dna.ctl-upload`  

Parameters:
* `T` - Method return type
* `Upload` - Method name

```cs
[HttpPost("[action]")]
[DisableRequestSizeLimit]
public async Task<${1:T}> ${2:Upload}() =>
    await db.${2:Upload}(
        Request.Form.Files,
        config.DirectoryBasePath,
        config.UrlBasePath
    );
```

**SignalR Hub Class**  

`dna.sgl-hub`  

Parameters:
* `Project` - Project namespace name
* `Data` - Hub name

```cs
using System;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.AspNetCore.SignalR;

namespace ${1:Project}.Web.Hubs
{
    public class ${2:Data}Hub : Hub
    {
        public override async Task OnDisconnectedAsync(Exception ex)
        {
            // Manage client disconnect

            await base.OnDisconnectedAsync(ex);
        }

        // ENTRY POINT
    }
}
```

**SignalR Hub Trigger**  

`dna.sgl-trigger`  

Parameters:
* `Action` - Trigger function name, PascalCase
* `T` - Function argument type
* `arg` - Function argument name
* `SendAll` - Clients method to execute
* `method` - Client function to execute

```cs
public async Task trigger${1:Action}(${2:T} ${3:arg})
{
    await Clients.${4:SendAll}(${3:arg}).SendAsync("${5:method}");
}
```  

### Angular Snippet Anatomy
[Back to Top](#contents)  

**Model Interface**  

`dna.model`  

Parameters:
* `Model` - Interface name, PascalCase

```ts
export interface INTERFACE {
    id: number;
    // ENTRY POINT
    createdDate: Date;
    isDeleted: boolean;
}
```

**Service Class**  

`dna.service`  

Parameters:
* `Object` - Service name, PascalCase

```ts
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { BehaviorSubject } from 'rxjs';
import { SnackerService } from './snacker.service';

@Injectable()
export class ${1:Object}Service {
    // ENTRY POINT

    constructor(
        private http: HttpClient,
        private snacker: SnackerService
    ) { }
}
```

**Service HTTP Function**  

`dna.http-func`

Parameters:
* `func` - Function name, camelCase
* `T` - Return value type
* `route` - API route
* `stream` - Stream to populate when data returns

```ts
${1:func} = () => this.http.get<${2:T}>(`/api/${3:route}`)
    .subscribe(
        data => this.${4:stream}.next(data),
        err => this.snacker.sendErrorMessage(err.error)
    );
```

**Service HTTP Promise**  

`dna.http-promise`  

Parameters:
* `func` - Function name, camelCase
* `arg` - Function argument name
* `T` - Function argument type
* `post` - HTTP function
* `route` - API route
* `success` - Message to send on success

```ts
${1:func} = (${2:arg}: ${3:T}): Promise<boolean> =>
    new Promise((resolve) => {
        this.http.${4:post}(`/api/${5:route}`, ${2:arg})
            .subscribe(
                () => {
                    this.snacker.sendSuccessMessage(${6:success});
                    // ENTRY POINT
                    resolve(true);
                },
                err => {
                    this.snacker.sendErrorMessage(err.error);
                    resolve(false);
                }
            )
    });
```  

**SignalR Service Class**  

`dna.sgl-service`  

Parameters:
* `Object` - Service name, PascalCase
* `url` - Hub route URL

```ts
import { Injectable } from '@angular/core';
import { HubConnectionBuilder } from '@aspnet/signalr';
import { BehaviorSubject } from 'rxjs';
import { SnackerService } from '../snacker.service';

@Injectable()
export class ${1:Object}SocketService {
    private connection = new HubConnectionBuilder()
        .withUrl('${2:url}')
        .build();

    private connected = new BehaviorSubject<boolean>(false);
    private error = new BehaviorSubject<any>(null);
    private trigger = new BehaviorSubject<boolean>(false);

    connected$ = this.connected.asObservable();
    error$ = this.error.asObservable();
    trigger$ = this.trigger.asObservable();

    constructor(
        private snacker: SnackerService
    ) {
        this.connection
            .start()
            .then(() => this.connected.next(true))
            .catch((err) => {
                this.connected.next(false);
                this.error.next(err);
                this.snacker.sendErrorMessage(err.error);
            });
    }

    // ENTRY POINT
}
```  

**SignalR Trigger Function**  

`dna.sgl-trigger`  

Parameters:
* `Func` - Trigger function name, postfixed to **trigger**
* `arg` - Trigger function argument name
* `T` - Trigger function argument type

```ts
trigger${1:Func} = async (${2:arg}: ${3:T}) =>
    this.connected.value &&
        await this.connection
            .invoke('trigger${1:Func}', ${2:arg});
```

**Component Class**  

`dna.component`  

Parameters:
* `Model` - Model dependency to import
* `selector` - Component selector, kebab-case
* `Object` - Component name, PascalCase  

```ts
import {
    Component,
    Input,
    Output,
    EventEmitter
} from '@angular/core';

import { ${1:Model} } from '../../models';

@Component({
    selector: '${2:selector}',
    templateUrl: '${2:selector}.component.html'
})
export class ${3:Object}Component {
    // ENTRY POINT
}
```

**Pipe Class**  

`dna.pipe`  

Parameters:
* `name` - Pipe name, camelCase
* `Object` - Pipe name, PascalCase
* `T` - Type for **value**
* `args` - Additional pipe arguments

```ts
import {
    Pipe,
    PipeTransform
} from '@angular/core';

@Pipe({
    name: '${1:name}'
})
export class ${2:Object}Pipe implements PipeTransform {
    transform(value: ${3:T}, ${4:args}) {
        // ENTRY POINT
    }
}
```

**Route Class**  

`dna.route`  

Parameters:
* `object` - Route short name, kebab-case
* `Object` - Route short name, PascalCase  

```ts
import {
    Component,
    OnInit
} from '@angular/core';

@Component({
    selector: '${1:object}-route',
    templateUrl: '${1:object}.component.html'
})
export class ${2:Object}Component implements OnInit {
    constructor(

    ) { }

    ngOnInit() {

    }

    // ENTRY POINT
}
```  

**Dialog Class**  

`dna.dialog`  

Parameters:
* `object` - Dialog short name, kebab-case
* `Object` - Dialog short name, PascalCase

```ts
import {
    MatDialogRef,
    MAT_DIALOG_DATA
} from '@angular/material';

import {
    Component,
    Inject
} from '@angular/core';

@Component({
    selector: '${1:object}-dialog',
    templateUrl: '${1:object}.dialog.html'
})
export class ${2:Object}Dialog {
    // ENTRY POINT
}
```  

**Observable Input**  

`dna.obs-input`  

Parameters:  
* `inputVar` - Template reference variable name
* `false` - Set the value of `@ViewChild`'s `static` option  

> Assumes a local `initialized` variable, as well as injecting a `core: CoreService` object that contains a `generateInputObservable(input: ElementRef)` function. See [StackBlitz - Docs ViewChild](https://stackblitz.com/edit/docs-viewchild) for an example.

```ts
@ViewChild('${1:inputVar}', { static: ${2: false} })
set ${1:inputVar}(input: ElementRef) {
    if (input && !this.initialized) {
        this.core.generateInputObservable(input)
            .subscribe(async val => {
                // ENTRY POINT
            });
        this.initialized = true;
    }
}
```

**Component Index**  

`dna.idx-component`  

Parameters:  
* `Component` - The initial component to load
* `dir` - The relative path to the initial component file
* `Object` - The name of the exported components array  

```ts
import { ${1:Component} } from '${2:dir}';
// ENTRY POINT

export const ${3:Object}Components = [
    ${1:Component}
];
```  

**Dialog Index**  

`dna.idx-dialog`  

Parameters:  
* `Dialog` - The initial dialog to load
* `dir` - The relative path to the initial dialog file
* `Object` - The name of the exported dialogs array  

```ts
import { ${1:Dialog} } from '${2:dir}';
// ENTRY POINT

export const ${3:Object}Dialogs = [
    ${1:Dialog}
];

export * from '${2:dir}';
```  

**Model Index**  

`dna.idx-model`  

> No parameters  

```ts
export * from '$0'; // ENTRY POINT @ $0
```  

**Pipe Index**  

`dna.idx-pipe`  

Parameters:
* `Pipe` - The initial pipe to load
* `dir` - The relative path to the initial pipe file
* `Object` - The name of the exported pipes array  

```ts
import { ${1:Pipe} } from '${2:dir}';
// ENTRY POINT

export const ${3:Object}Pipes = [
    ${1:Pipe}
];
```  

**Route Index**  

`dna.idx-route`  

Parameters:
* `RouteComponent` - The initial route component to load
* `dir` - The relative path to the initial route component file
* `path` - The route the initial route component should resolve to

```ts
import { Route } from '@angular/router';
import { ${1:RouteComponent} } from '${2:dir}';
// ENTRY POINT

export const RouteComponents = [
    ${1:RouteComponent}
];

export const Routes: Route[] = [
    { path: '${3:path}', component: ${1:RouteComponent} },
    { path: '', redirectTo: '${3:path}', pathMatch: 'full' },
    { path: '**', redirectTo: '${3:path}', pathMatch: 'full' }
];
```  

**Child Route Index**  

`dna.idx-child-route`  

Parameters:
* `RouteComponent` - The initial route component to load
* `dir` - The relative path to the initial route component file
* `Object` - The name of the exported routes / route components arrays
* `path` - The route the initial route component should resolve to  

```ts
import { Route } from '@angular/router';
import { ${1:RouteComponent} } from '${2:dir}';
// ENTRY POINT

export const ${3:Object}Components = [
    ${1:RouteComponent}
];

export const ${3:Object}Routes: Route[] = [
    { path: '${4:path}', component: ${1:RouteComponent} },
    { path: '', redirectTo: '${4:path}', pathMatch: 'prefix' },
    { path: '**', redirectTo: '${4:path}', pathMatch: 'prefix' }
];
```  

**Service Index**  

`dna.idx-service`  

Parameters:
* `Service` - The initial service to load
* `dir` - The relative path to the initial service file  

> Any service loaded into the Services array is added to a `ServicesModule.providers` array, thus making it initially globally scoped.  

```ts
import { ${1:Service} } from '${2:dir}';
// ENTRY POINT

export const Services = [
    ${1:Service}
];

export * from '${2:dir}';
```

#### Angular Template Anatomy  
[Back to Top](#contents)  

**Dialog Template**  

`dna.dialog`  

Parameters:
* `title` - Dialog title text

```html
<div class="mat-typography">
    <h2 mat-dialog-title>${1:title}</h2>
    <mat-dialog-content>
      <!-- ENTRY POINT -->
    </mat-dialog-content>
    <mat-dialog-actions>
        <button mat-button
                mat-dialog-close>Cancel</button>
    </mat-dialog-actions>
</div>
```

**Card Shell**  

`dna.card-shell`  

Parameters:
* `elevated` - Additional classes
* `layout` - Flex layout
* `align` - Flex layout alignment  

```html
<section class="background card ${1:elevated}"
         fxLayout="${2:layout}"
         fxLayoutAlign="${3:align}">
    <!-- ENTRY POINT -->
</section>
```

**Flex Container**  

`dna.flex-container`  

Parameters:
* `layout` - Flex layout
* `align` - Flex layout alignment  

```html
<section fxLayout="${1:layout}"
         fxLayoutAlign="${2:align}"
         class="container">
    <!-- ENTRY POINT -->
</section>
```

**Async Container**  

`dna.async-container`  

Parameters:
* `stream` - Stream to subscribe to with the `async` pipe
* `data` - Resulting value of data resolved by `stream`

```html
<ng-container *ngIf="${1:stream} | async as ${2:data} else loading">
    <!-- ENTRY POINT -->
</ng-container>
```

**Loading Template**

`dna.loading-template`  

Parameters:
* `indeterminate` - MatProgressBar mode
* `accent` - Material theme color

```html
<ng-template #loading>
    <mat-progress-bar mode="${1:indeterminate}"
                      color="${2:accent}"></mat-progress-bar>
</ng-template>
```

**Searchbar**  

`dna.searchbar`  

Parameters:
* `Search` - Searchbar label
* `1` - Minimum number of characters before `search` function is executed
* `searchFunction` - Function to execute on `search`
* `clearFunction` - Function to execute when searchbar is cleared

> Assumes a SearchbarComponent exists with the specified input / output properties. See [StackBlitz - Searchbar Example]() for this [component definition](https://stackblitz.com/edit/searchbar-example?file=src%2Fapp%2Fcomponents%2Fsearchbar%2Fsearchbar.component.ts) and [implementation](https://stackblitz.com/edit/searchbar-example?file=src%2Fapp%2Froutes%2Fhome%2Fhome.component.html).

```html
<searchbar label="${1:Search}"
           [minimum]="${2:1}"
           (search)="${3:searchFunction}"
           (clear)="${4:clearFunction}"></searchbar>
```

**Material Select**

`dna.mat-select`  

Parameters:
* `Label` - Select label
* `model` - Data binding target for the select element
* `changeFunction()` - Function to execute when the selection is changed
* `o` - Variable representing a single option from a collection of objects
* `data` - A collection of objects to iterate when populating select options
* `val` - Value that a select option represents from the `o` variable
* `display` - Property / Properties to display from the `o` variable in the select list  

```html
<mat-form-field>
    <mat-label>${1:Label}</mat-label>
    <mat-select [(ngModel)]="${2:model}"
                (selectionChange)="${3:changeFunction()}">
        <mat-option *ngFor="let ${4:o} of ${5:data}"
                    [value]="${6:val}">
            {{${7:display}}}
        </mat-option>
    </mat-select>
</mat-form-field>
```

**Material Input**  

`dna.mat-input`  

Parameters:
* `Label` - Input label
* `model` - Data binding target for the input element  

```html
<mat-form-field>
    <mat-label>${1:Label}</mat-label>
    <input matInput 
           [(ngModel)]="${2:model}" />
</mat-form-field>
```  

**Material Input Template Reference Variable**  

`dna.mat-input-trv`

Parameters:
* `Label` - Input label
* `model` - Data binding target for the input element
* `varName` - Template reference variable name  

```html
<mat-form-field>
    <mat-label>${1:Label}</mat-label>
    <input matInput
           [(ngModel)]="${2:model}"
           #${3:varName} />
</mat-form-field>
```

**Material Textarea**  

`dna.mat-textarea`  

Parameters:
* `Label` - Textarea label
* `model` - Data binding target for the textarea element
* `4` - Autosize minimum rows
* `8` - Autosize maximum rows

```html
<mat-form-field>
    <mat-label>${1:Label}</mat-label>
    <textarea matInput
              mat-autosize
              [(ngModel)]="${2:model}"
              [matAutosizeMinRows]="${3:4}"
              [matAutosizeMaxRows]="${4:8}"></textarea>
</mat-form-field>
```

**Material Slider**  

`dna.mat-slider`  

Parameters:
* `model` - Data binding target for the mat-slider element
* `min` - Minimum value
* `max` - Maximum value
* `true` - Show thumblabel
* `step` - Step values at which thumb will snap
* `interval` - How often ticks are shown on the slider
* `inputFunction` - Function to call as slider values change  

```html
<mat-slider [value]="${1:model}"
            [min]="${2:min}"
            [max]="${3:max}"
            [thumbLabel]="${4:true}"
            [step]="${5:step}"
            [tickInterval]="${6:interval}"
            (input)="${7:inputFunction}"></mat-slider>
```

**Material Slide Toggle**  

`dna.mat-slide-toggle`  

Parameters:
* `model` - Data binding target for the mat-slide-toggle element
* `Label` - Slide toggle label

```html
<mat-slide-toggle [(ngModel)]="${1:model}">${2:Label}</mat-slide-toggle>
```

**Material Menu**

`dna.mat-menu`  

Parameters:
* `menu` - Menu reference variable name
* `menu_icon` - Material icon to use for the menu button
* `clickFunction` - Function to execute for the initial menu item
* `label` - Initial menu item label

```html
<button mat-icon-button
        [matMenuTriggerFor]="${1:menu}">
    <mat-icon>${2:menu_icon}</mat-icon>
</button>
<mat-menu #${1:menu}="matMenu">
    <button mat-menu-item
            (click)="${3:clickFunction}">
        {{${4:label}}}
    </button>
    <!-- ENTRY POINT -->
</mat-menu>
```

**Material Tab Nav**

`dna.mat-tab-nav`

Parameters:
* `scrolled` - Additional class to apply to the nav element.
* `link` - Initial tab link
* `active` - Initial tab active class
* `Label` - Initial tab label

```html
<nav mat-tab-nav-bar
     class="${1:scrolled}">
    <a mat-tab-link
       routerLink="${2:link}"
       routerLinkActive="${3:active}">
        ${4:Label}
    </a>
    <!-- ENTRY POINT -->
</nav>
<router-outlet></router-outlet>
```