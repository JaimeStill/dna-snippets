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
Dialog Template | `dna.dialog` | HTML

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