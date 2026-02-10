| JS input | Handlebars output | Category |
|:--------:|:-----------------:|:--------:|
|${varName} | {{varName}}      | substitution |
|{raw(varName)} | {{{varName}}} | unescape substitution |
|if(cond){...} else {...} | {{#if cond}} ... {{else}} ... {{/if}} | conditional
|if(cond) { ... } else if(cond) { ... } else { ... } |{{#if cond}} ... {{else cond}} ... {{else}} ... {{/if}} | conditional
|if(!cond){...} | {{#unless cond}} ... {{/unless}} | negated condition | 
|if(a === b){...} | {{#equals a "b"}} ... {{/equals}} | equality check
|if(a !== b) { ... } | {{#notEquals a "b"}} ... {{/notEquals}} | inequality check | 
|if(a > b) { ... } | {{#greaterThan a b}} ... {{/greaterThan}} | comparison | 
|if(a < b) { ... }| {{#lessThan a b}} ... {{/lessThan}} | comparison | 
|if(a && b) { ... }| {{#and a b}} ... {{/and}} | logical AND |
|if(a OR b ) { ... } | {{#or a b}} ... {{/or}} | logical OR | 
|collection.forEach(item => { ... }) | {{#each collection}} ... (this) ... {{/each}} | iteration |
| name ?? "Customer" | {{insert name "default=Customer"}} | default values|
| formatDate(field, "MM/DD/YYYY") | {{formatDate field "MM/DD/YYYY"}} | Date formatting | 
|collection.length | (length collection) | length sub-expression |

### Special Cases
#### 1. `@root` case
Handlebars has block scoping. This means that when we enter a block with #each or #equals handlebars changes the context (the `this` binding). So inside `{{#each user.orders}}` the context becomes each individual order object (this means that each item or 'order' has its own scope). So `{{this.item}}` works because item its part of the orders scope and `{{user.name}}` doesn't work because its not part of the current scope.

How to solve this? (pseudocode)

`emitVar(varName, currentScopeDepth):`<br>
`if currentScopeDepth === 0:`<br>
`return "{{varname}}"`<br>
`if varName starts with "this.":`<br>
`return "{{varname}}"`<br>
`else:`<br>
`return "{{@root.varName}}"`


