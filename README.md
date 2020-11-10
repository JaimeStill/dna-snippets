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
        * [Angular Style Anatomy](#angular-style-anatomy)

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
DbSet Property | `dna.ent-dbset` | C#
Entity KeyMap | `dna.ent-keymap` | C#
Extension Class | `dna.ext-class` | C#
Extension Baseline | `dna.ext-base` | C#
Extension Method | `dna.ext-method` | C#
Extension Query Method | `dna.ext-query` | C#
Extension Get Method | `dna.ext-get` | C#
Extension Entity Method | `dna.ext-entity` | C#
Extensions Validate Method | `dna.ext-validate` | C#
Extensions Validate Async Method | `dna.ext-validate-async` | C#
Middleware Class | `dna.mw-class` | C#
Middleware Extension | `dna.mw-extension` | C#
Controller Class | `dna.ctl-class` | C#
Controller Baseline | `dna.ctl-base` | C#
Controller Query Method | `dna.ctl-query` | C#
Controller Get Method | `dna.ctl-get` | C#
Controller Get Method Routed | `dna.ctl-get-routed` | C#
Controller Post Method | `dna.ctl-post` | C#
Controller Upload Method | `dna.ctl-upload` | C#
SignalR Hub Class | `dna.sgl-hub` | C#
SignalR Hub Trigger | `dna.sgl-trigger` | C#

### Angular Snippets
[Back to Top](#contents)  

Type | Name | FileType
-----|------|---------
Model Interface | `dna.model` | TypeScript
Reactive Model Interface | `dna.rx-model` | TypeScript
Service Class | `dna.service` | TypeScript
Data Source | `dna.source` | TypeScript
Service API | `dna.api` | TypeScript
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
Drag and Drop Selector | `dna.dnd-selector` | TypeScript
Dialog Template | `dna.dialog` | HTML
Card Shell | `dna.card-shell` | HTML
Flex Container | `dna.flex-container` | HTML
Async Container | `dna.async-container` | HTML
Loading Template | `dna.loading-template` | HTML
Searchbar | `dna.searchbar` | HTML
Material Select | `dna.mat-select` | HTML
Material Select Change | `dna.mat-select-change` | HTML
Material Input | `dna.mat-input` | HTML
Material Input Template Reference Variable | `dna.mat-input-trv` | HTML
Material Textarea | `dna.mat-textarea` | HTML
Material Datepicker | `dna.mat-datepicker` | HTML
Material Slider | `dna.mat-slider` | HTML
Material Slide Toggle | `dna.mat-slide-toggle` | HTML
Material Menu | `dna.mat-menu` | HTML
Material Tab Nav | `dna.mat-tab-nav` | HTML
Material Route Tab | `dna.mat-route-tab` | HTML
Drag and Drop Selector | `dna.dnd-selector` | HTML
Reactive Checkbox | `dna.rx-checkbox` | HTML
Reactive Datepicker | `dna.rx-datepicker` | HTML
Reactive Input | `dna.rx-input` | HTML
Reactive Radio | `dna.rx-radio` | HTML
Reactive Select | `dna.rx-select` | HTML
Reactive Select Change | `dna.rx-select-change` | HTML
Reactive Slide Toggle | `dna.rx-slide-toggle` | HTML
Reactive Slider | `dna.rx-slider` | HTML
Reactive Textarea | `dna.rx-textarea` | HTML
Drag and Drop Selector | `dna.dnd-selector` | CSS

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
    }
}
```

**DbSet Property**

`dna.ent-dbset`

Parameters:  
* `T` - Entity type
* `Plural` - Pluralized entity name

```cs
public DbSet<${1:T}> ${2:Plural} { get; set; }
```

**Entity Key Map**

`dna.ent-keymap`

Parameters:  
* `T` - Entity type
* `Many` - Many-sided property name

```cs
modelBuilder
    .Entity<${1:T}>()
    .HasMany(x => x.${2:Many})
    .WithOne(x => x.${1:T})
    .HasForeignKey(x => x.${1:T}Id)
    .IsRequired()
    .OnDelete(DeleteBehavior.Restrict);
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

using ${1:Project}.Core;
using ${1:Project}.Core.ApiQuery;
using ${1:Project}.Data.Entities;

namespace ${1:Project}.Data.Extensions
{
    public static class ${2:Entity}Extensions
    {
        // ENTRY POINT
    }
}
```

**Extension Class Baseline**

`dna.ext-base`

Parameters:
* `Project` - Project namespace root
* `Singular` - Singular capitalized entity name
* `plural` - Pluralized lowercased entity name
* `Prop` - Initial search property for Search / Validate extension methods
* `Plural` - Pluralized capitalized entity name
* `singular` - Singular lowercased entity name
* `prop` - Lowercased property name for exception message

```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

using Microsoft.EntityFrameworkCore;

using ${1:Project}.Core;
using ${1:Project}.Core.ApiQuery;
using ${1:Project}.Data.Entities;

namespace ${1:Project}.Data.Extensions
{
    public static class ${2:Singular}Extensions
    {
        static IQueryable<${2:Singular}> Search(this IQueryable<${2:Singular}> ${3:plural}, string search) =>
            ${3:plural}.Where(x => x.${4:Prop}.ToLower().Contains(search.ToLower()));

        public static async Task<QueryResult<${2:Singular}>> Query${5:Plural}(
            this AppDbContext db,
            string page,
            string pageSize,
            string search,
            string sort
        ) {
            var container = new QueryContainer<${2:Singular}>(
                db.${5:Plural},
                page, pageSize, search sort
            );

            return await container.Query((${3:plural}, s) => ${3:plural}.Search(s));
        }

        public static async Task<${2:Singular}> Get${2:Singular}(this AppDbCOntext db, int id) =>
            await db.${5:Plural}
                .FindAsync(id);

        public static async Task Add${2:Singular}(this AppDbCOntext db, ${2:Singular} ${6:singular})
        {
            if (await ${6:singular}.Validate(db))
            {
                await db.${5:Plural}.AddAsync(${6:singular});
                await db.SaveChangesAsync();
            }
        }

        public static async Task Update${2:Singular}(this AppDbContext db, ${2:Singular} ${6:singular})
        {
            if (await ${6:singular}.Validate(db))
            {
                db.${5.Plural}.Update(${6:singular});
                await db.SaveChangesAsync();
            }
        }

        public static async Task Remove${2:Singular}(this AppDbContext db, ${2:Singular} ${6:singular})
        {
            db.${5:Plural}.Remove(${6:singular});
            await db.SaveChangesAsync();
        }

        static async Task<bool> Validate(this ${2:Singular} ${6:singular}, AppDbContext db)
        {
            if (string.IsNullOrEmpty(${6:singular}.${4:Prop}))
            {
                throw new AppException("${2:Singular} must have a ${7:prop}", ExceptionType.Validation);
            }

            var check = await db.${5:Plural}
                .FirstOrDefaultAsync(x =>
                    x.Id != ${6:singular}.Id &&
                    x.${4:Prop}.ToLower() == ${6:singular}.${4:Prop}.ToLower()
                );

            if (check != null)
            {
                throw new AppException($"{${6:singular}.${4:Prop}} is already a ${2:Singular}", ExceptionType.Validation);
            }
            
            return true;
        }

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

**Extension Query Method**

`dna.ext-query`

Parameters:  
* `T`: Entity type
* `Plural`: Pluralized capitalized entity name
* `plural`: Pluralized lowercase entity name

```cs
public static async Task<QueryResult<${1:T}>> Query${2:Plural}(
    this AppDbContext db,
    string page,
    string pageSize,
    string search,
    string sort
) {
    var container = new QueryContainer<${1:T}>(
        db.${2:Plural}/* ENTRY POINT */,
        page, pageSize, search, sort
    );

    return await container.Query((${3:plural}, s) => ${3:plural}.Search(s));
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

**Controller Class Baseline**

`dna.ctl-base`

Parameters:  
* `Project` - Project namespace name
* `Singular` - Singular capitalized entity name
* `Plural` - Pluralized capitalized entity name
* `singular` - Singular lowercase entity name

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
    public class ${2:Singular}Controller : Controller
    {
        private AppDbContext db;

        public ${2:Singular}Controller(AppDbContext db)
        {
            this.db = db;
        }

        [HttpGet("[action]")]
        [ProducesResponseType(typeof(QueryResult<${2:Singular}>), 200)]
        public async Task<IActionResult> Query${3:Plural}(
            [FromQuery]string page,
            [FromQuery]string pageSize,
            [FromQuery]string search,
            [FromQuery]string sort
        ) => Ok(await db.Query${3:Plural}(page, pageSize, search, sort));

        [HttpGet("[action]/{id}")]
        public async Task<${2:Singular}> Get${2:Singular}([FromRoute]int id) => await db.Get${2:Singular}(id);

        [HttpPost("[action]")]
        public async Task Add${2:Singular}([FromBody]${2:Singular} ${4:singular}) => await db.Add${2:Singular}(${4:singular});

        [HttpPost("[action]")]
        public async Task Update${2:Singular}([FromBody]${2:Singular} ${4:singular}) => await db.Update${2:Singular}(${4:singular});

        [HttpPost("[action]")]
        public async Task Remove${2:Singular}([FromBody]${2:Singular} ${4:singular}) => await db.Remove${2:Singular}(${4:singular});
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

**Controller Get Method Routed**

`dna.ctl-get-routed`

Parameters:
* `param` - Routed parameter name
* `T` - Action method return type
* `Get` - Action method name
* `type` - Type of the routed parameter

```cs
[HttpGet("[action]/{${1:param}}")]
public async Task<${2:T}> ${3:Get}([FromRoute]${4:type} ${1:param}) => await db.${3:Get}(${1:param});
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
export interface ${1:Model} {
    id: number;
    // ENTRY POINT
}
```

**Reactive Model Interface**

`dna.rx-model`

Parameters:  
* `Model` - Interface name, PascalCase
* `model` - Interface name, camelCase

```ts
import {
    FormBuilder,
    FormGroup,
    Validators
} from '@angular/forms';

export interface ${1:Model} {
    id: number,
    $0
}

export const ${1:Model}Form = (${2:model}: ${1:Model}, fb: FormBuilder): FormGroup =>
    fb.group({
        id: ${2:model}.id
    })
```

**Service Class**  

`dna.service`  

Parameters:
* `../../services` - Relative path to library `services` module
* `../../config` - Relative path to library `config` module
* `T` - Entity type or service name

```ts
import {
    Injectable,
    Optional
} from '@angular/core';

import { HttpClient } from '@angular/common/http';
import { BehaviorSubject } from 'rxjs';
import { SnackerService } from '${1:../../services}';
import { ServerConfig } from '${2:../../config}';

@Injectable()
export class ${3:T}Service {
    // ENTRY POINT

    constructor(
        private http: HttpClient,
        private snacker: SnackerService,
        @Optional() private config: ServerConfig
    ) { }
}
```

**Data Source**

`dna.source`

Parameters:  
* `Singular` - Entity type capitalized
* `$2` - Property names to render in a table. Provided as strings in `columns` array.
* `prop` - Default sorting property name
* `singular` - Entity type lowercase
* `Plural` - Pluralized entity name capitalized

```ts
import {
    Injectable,
    Optional
} from '@angular/core';

import {
    QueryService,
    SnackerService
} from '../../../services';

import { DataSource } from '@angular/cdk/table';
import { HttpClient } from '@angular/common/http';
import { ServerConfig } from '../../../config';
import { ${1:Singular} } from '../../models';

@Injectable()
export class ${1:Singular}Source extends QueryService<${1:Singular}> implements DataSource<${1:Singular}> {
    columns = [$2];

    constructor(
        protected http: HttpClient,
        protected snacker: SnackerService,
        @Optional() private config: ServerConfig
    ) {
        super(http, snacker);
        this.sort = {
            isDescending: false,
            propertyName: '${3:prop}'
        };

        this.baseUrl = `${this.config.api}${4:singular}/query${5:Plural}`;
    }

    track${5:Plural} = (${4:singular}: ${1:Singular}) => ${4:singular}.id;
}
```

**Service API**

`dna.api`

Parameters:  
* `Singular` - Entity name capitalized
* `singular` - Entity name lowercase
* `id` - Parameter to allow `id` to be interpolated in the `http.get` string
* `prop` - Property used in success messages

```ts
import {
    Injectable,
    Optional
} from '@angular/core';

import { HttpClient } from '@angular/common/http';
import { BehaviorSubject} from 'rxjs';
import { SnackerService } from '../../services';
import { ServerConfig } from '../../config';
import { ${1:Singular} } from '../models';

@Injectable()
export class ${1:Singular}Service {
    private ${2:singular} = new BehaviorSubject<${1:Singular}>(null);
    ${2:singular}$ = this.${2:singular}.asObservable();

    constructor(
        private http: HttpClient,
        private snacker: SnackerService,
        @Optional() private config: ServerConfig
    ) { }

    get${1:Singular} = (id: number): Promise<${1:Singular}> => new Promise((resolve) => {
        this.http.get<${1:Singular}>(`${this.config.api}${2:singular}/get${1:Singular}/${3:id}`)
            .subscribe(
                data => {
                    this.${2:singular}.next(data);
                    resolve(data);
                },
                err => {
                    this.snacker.sendErrorMessage(err.error);
                    resolve(null);
                }
            );
    })

    add${1:Singular} = (${2:singular}: ${1:Singular}): Promise<boolean> => new Promise((resolve) => {
        this.http.post(`${this.config.api}${2:singular}/add${1:Singular}`, ${2:singular})
            .subscribe(
                () => {
                    this.snacker.sendSuccessMessage(`${${2:singular}.${4.prop}} successfully created`);
                    resolve(true);
                },
                err => {
                    this.snacker.sendErrorMessage(err.error);
                    resolve(false);
                }
            );
    })

    update${1:Singular} = (${2:singular}: ${1:Singular}): Promise<boolean> => new Promise((resolve) => {
        this.http.post(`${this.config.api}${2:singular}/update${1:Singular}`, ${2:singular})
            .subscribe(
                () => {
                    this.snacker.sendSuccessMessage(`${${2:singular}.${4:prop}} successfully updated`);
                    resolve(true);
                },
                err => {
                    this.snacker.sendErrorMessage(err.error);
                    resolve(false);
                }
            );
    })

    remove${1:Singular} = (${2:singular}: ${1:Singular}): Promise<boolean> => new Promise((resolve) => {
        this.http.post(`${this.config.api}${2:singular}/remove${1:Singular}`, ${2:singular})
            .subscribe(
                () => {
                    this.snacker.sendSuccessMessage(`${${2:singular}.${4:prop}} successfully removed`);
                    resolve(true);
                },
                err => {
                    this.snacker.sendErrorMessage(err.error);
                    resolve(false);
                }
            );
    })
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

**Drag and Drop Selector**  

`dna.dnd-selector`  

Parameters:
* `Object` - Interface of the object represented by drag and drop arrays and Selector component name, PascalCased
* `object` - Name for the selector component, kebab-cased
* `available` - Array of objects available to add
* `assigned` - Array of objects currently assigned and can be removed by dragging to `available`  

```ts
import {
    Component,
    Input,
    Output,
    EventEmitter
} from '@angular/core';

import {
    CdkDragDrop,
    moveItemInArray,
    transferArrayItem
} from '@angular/cdk/drag-drop';

import { ${1:Object} } from '../../models';

@Component({
    selector: '${2:object}-selector',
    templateUrl: '${2:object}-selector.component.html',
    styleUrls: ['${2:object}-selector.component.css']
})
export class ${1:Object}SelectorComponent {
    @Input() ${3:available}: ${1:Object}[];
    @Input() ${4:assigned}: ${1:Object}[];
    @Input() pending = false;
    @Output() save = new EventEmitter<${1:Object}[]>();

    drop = (event: CdkDragDrop<${1:Object}[]>) => {
        event.previousContainer !== event.container ?
            transferArrayItem(
                event.previousContainer.data,
                event.container.data,
                event.previousIndex,
                event.currentIndex
            ) :
            moveItemInArray(
                event.container.data,
                event.previousIndex,
                event.currentIndex
            );
    }
}
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
        <button mat-stroked-button
                mat-dialog-close>Cancel</button>
    </mat-dialog-actions>
</div>
```

**Card Shell**  

`dna.card-shell`  

Parameters:
* `background card elevated` - Classes
* `layout` - Flex layout
* `align` - Flex layout alignment  

```html
<section class="${1:background card elevated}"
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
* `container` - Classes

```html
<section fxLayout="${1:layout}"
         fxLayoutAlign="${2:align}"
         class="${3:container}">
    <!-- ENTRY POINT -->
</section>
```

**Async Container**  

`dna.async-container`  

Parameters:
* `stream` - Stream to subscribe to with the `async` pipe
* `data` - Resulting value of data resolved by `stream`
* `loading` - Loading template name

```html
<ng-container *ngIf="${1:stream} | async as ${2:data} else ${3:loading}">
    <!-- ENTRY POINT -->
</ng-container>
```

**Loading Template**

`dna.loading-template`  

Parameters:
* `loading` - Loading template reference variable name
* `indeterminate` - MatProgressBar mode
* `accent` - Material theme color

```html
<ng-template #${1:loading}>
    <mat-progress-bar mode="${2:indeterminate}"
                      color="${3:accent}"></mat-progress-bar>
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
* `o` - Variable representing a single option from a collection of objects
* `data` - A collection of objects to iterate when populating select options
* `val` - Value that a select option represents from the `o` variable
* `display` - Property / Properties to display from the `o` variable in the select list  

```html
<mat-form-field>
    <mat-label>${1:Label}</mat-label>
    <mat-select [(ngModel)]="${2:model}">
        <mat-option *ngFor="let ${3:o} of ${4:data}"
                    [value]="${5:val}">
            {{${6:display}}}
        </mat-option>
    </mat-select>
</mat-form-field>
```

**Material Select Change**

`dna.mat-select-change`  

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

**Material Datepicker**

`dna.mat-datepicker`

Parameters:  
* `Label` - Input label
* `model` - Data binding target for the input element
* `picker` - Template Reference Variable name for `mat-datepicker`

```html
<mat-form-field>
    <mat-label>${1:Label}</mat-label>
    <input [(ngModel)]="${2:model}" matInput [matDatepicker]="${3:picker}">
    <mat-datepicker-toggle matSuffix [for]="${3:picker}"></mat-datepicker-toggle>
    <mat-datepicker #${3:picker}></mat-datepicker>
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

**Material Route Tab**

`dna.mat-route-tab`

Parameters:
* `link` - Initial tab link
* `active` - Initial tab active class
* `Label` - Initial tab label

```html
<a mat-tab-link
   routerLInk="${1:link}"
   routerLinkActive="${3:active}">
  ${3:Label}
</a>
```

**Drag and Drop Selector**  

`dna.dnd-selector`  

Parameters:
* `Available` - Label for objects available for adding
* `available` - Collection of objects available for adding
* `x` - Variable to represent a singular object from `available` in an iteration
* `x.display` - Property to display for `x`
* `Assigned` - Label for objects already added / available for removal
* `assigned` - Collection of objects already added / available for removal
* `y` - Variable to represent a singular object from `assigned` in an iteration
* `y.display` - Property to display for `y`  

```html
<button mat-stroked-button
        [disabled]="pending"
        [style.margin.px]="8"
        (click)="save.emit(${6:assigned})">
    Save
</button>
<section fxLayout="row"
         fxLayoutAlign="start start">
    <section fxLayout="column"
             fxLayoutAlign="start stretch"
             fxFlex
             [style.margin-right.px]="4">
        <p class="mat-title">${1:Available}</p>
        <section cdkDropList
                 #list="cdkDropList"
                 [cdkDropListData]="${2:available}"
                 [cdkDropListConnectedTo]="[selected]"
                 class="container drop-container"
                 (cdkDropListDropped)="drop($event)">
            <section *ngFor="let ${3:x} of ${2:available}"
                     class="background card container elevated clickable"
                     cdkDrag">
                <div class="drag-placeholder" *cdkDragPlaceholder></div>
                <p>{{${4:x.display}}}</p>
            </section>
        </section>
    </section>
    <section fxLayout="column"
             fxLayoutAlign="start stretch"
             fxFlex
             [style.margin-right.px]="4">
        <p class="mat-title">${5:Assigned}</p>
        <section cdkDropList
                 #selected="cdkDropList"
                 [cdkDropListData]="${6:assigned}"
                 [cdkDropListConnectedTo]="[list]"
                 class="container drop-container"
                 (cdkDropListDropped)="drop($event)">
            <section *ngFor="let ${7:y} of ${6:assigned}"
                     class="background card container elevated clickable"
                     cdkDrag">
                <div class="drag-placeholder" *cdkDragPlaceholder></div>
                <p>{{${8:y.display}}}</p>
            </section>
        </section>
    </section>
</section>
```

**Reactive Checkbox**

`dna.rx-checkbox`

Parameters:  
* `control` - Form control name
* `true` - Indeterminate value
* `Label` - Checkbox label

```html
<mat-checkbox formControlName="${1:control}" [indeterminate]="${2:true}">${3:Label}</mat-checkbox>
```

**Reactive Datepicker**

`dna.rx-datepicker`

Parameters:  
* `Label` - Input label
* `control` - Form control name
* `picker` - Template Reference Variable for `mat-datepicker`

```html
<mat-form-field>
    <mat-label>${1:Label}</mat-label>
    <input formControlName="${2:control}" matInput [matDatepicker]="${3:picker}">
    <mat-datepicker-toggle matSuffix [for]="${3:picker}"></mat-datepicker-toggle>
    <mat-datepicker #${3:picker}></mat-datepicker>
</mat-form-field>
```

**Reactive Input**

`dna.rx-input`

Parameters:  
* `Label` - Input label
* `control` - Form control name

```html
<mat-form-field>
    <mat-label>${1:Label}</mat-label>
    <input formControlName="${2:control}" matInput>
</mat-form-field>
```

**Reactive Radio**

`dna.rx-radio`

Parameters:  
* `Label` - Input label
* `control` - Form control name
* `column` - Flex layout alignment (`column` or `row`)
* `8px` - Flex layout gap
* `opt` - Iteration variable for the `data` collection
* `data` - Collection of data for the radio group
* `value` - Value each radio button represents
* `display` - Value to display for each radio button label

```html
<label>${1:Label}</label>
<mat-radio-group formControlName="${2:control}" fxLayout="${3:column}" fxLayoutGap="${4:8px}">
    <mat-radio-button *ngFor="let ${5:opt} of ${6:data}" [value]="${7:value}">{{${8:display}}}</mat-radio-button>
</mat-radio-group>
```

**Reactive Select**

`dna.rx-select`

Parameters:  
* `Label` - Input label
* `control` - Form control name
* `opt` - Iteration variable for the `data` collection
* `data` - Collection of data for the select options
* `value` - Value each option represents
* `display` - Value to display for each option

```html
<mat-form-field>
    <mat-label>${1:Label}</mat-label>
    <mat-select formControlName="${2:control}">
        <mat-option *ngFor="let ${3:opt} of ${4:data}" [value]="${5:value}">{{${6:display}}}</mat-option>
    </mat-select>
</mat-form-field>
```

**Reactive Select Change**

`dna.rx-select-change`

Parameters:  
* `Label` - Input label
* `control` - Form control name
* `changeFunction()` - Function to execute when the selection is changed
* `opt` - Iteration variable for the `data` collection
* `data` - Collection of data for the select options
* `value` - Value each option represents
* `display` - Value to display for each option

```html
<mat-form-field>
    <mat-label>${1:Label}</mat-label>
    <mat-select formControlName="${2:control}" (selectionChange)="${3:changeFunction()}">
        <mat-option *ngFor="let ${4:opt} of ${5:data}" [value]="${6:value}">{{${7:display}}}</mat-option>
    </mat-select>
</mat-form-field>
```

**Reactive Slide Toggle**

`dna.rx-slide-toggle`

Parameters:  
* `control` - Form control name
* `Label` - Slide toggle label

```html
<mat-slide-toggle formControlName="${1:control}">${2:Label}</mat-slide-toggle>
```

**Reactive Slider**

`dna.rx-slider`

Parameters:  
* `8px` - Layout gap for contained elements
* `Label` - Slider label
* `control` - Form control name
* `min` - Slider min value
* `max` - Slider max value
* `step` - Interval of change
* `true` - Whether or not to render the thumb label
* `value` - Property that displays the value held by the slider

```html
<section fxLayout="row" fxLayoutAlign="start center" fxLayoutGap="${1:8px}">
    <span>${2:Label}</span>
    <mat-slider formControlName="${3:control}" [min]="${4:min}" [max]="${5:max}" [step]="${6:step}" [thumbLabel]="${7:true}"></mat-slider>
    <span>{{${8:value}}}</span>
</section>
```

**Reactive Textarea**

`dna.rx-textarea`

Parameters:  
* `Label` - Textarea label
* `control` - Form control name
* `min` - Min textarea rows
* `max` - Max textarea rows

```html
<mat-form-field>
    <mat-label>${1:Label}</mat-label>
    <textarea formControlName="${2:control}" matInput mat-autosize [matAutosizeMinRows]="${3:min}" [matAutosizeMaxRows]="${4:max}"></textarea>
</mat-form-field>
```

#### Angular Style Anatomy  
[Back to Top](#contents)  

**Drag and Drop Selector**  

`dna.dnd-selector`  

> No parameters  

```css
.drop-container {
    border: dotted 1px #ccc;
    min-height: 50px;
}

.cdk-drag-animating {
    transition: transform 250ms cubic-bezier(0, 0, 0.2, 1);
}

.drop-container.cdk-drop-list-dragging .drop-container:not(.cdk-drag-placeholder) {
    transition: transform 250ms cubic-bezier(0, 0, 0.2, 1);
}

.drag-placeholder {
    background: #eee;
    border: dotted 1px #ccc;
    min-height: 50px;
    transition: transform 250ms cubic-bezier(0, 0, 0.2, 1);
}

.cdk-drag-preview {
    font-family: 'Roboto';
    background-color: rgba(247, 247, 247, .7);
}
```