| JS input | Handlebars output | Category |
|:--------:|:-----------------:|:--------:|
|{varName} | {{varName}}      | substitution |
|{raw(varName)} | {{{varName}}} | unescape substitution |
|if(cond){...} else {...} | {{#if cond}} ... {{else}} ... {{/if}} | conditional
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

