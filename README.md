# ng2-tinymce-alt

Angular 2 component for TinyMCE MCE WYSIWYG editor based on 'angular2-tinymce'(https://github.com/Ledzz/angular2-tinymce)".
It's alternative package, when use angular-cli - fixed error "Cannot find module 'tinymce/tinymce.js'".
 
## Usage

First, install package via npm:
```
npm install --save angular2-tinymce
```

Then copy lightgray skin from [here] (https://github.com/Ledzz/angular2-tinymce/tree/master/demo/assets/tinymce/skins/lightgray) to the `/assets` folder. So, i.e. there must be available `/assets/tinymce/skins/lightgray/skin.min.css` file.
You can override skin path by specifying `skin_url` option (default `/assets/tinymce/skins/lightgray`).

Add these in your angular-cli.json:

"scripts": [
	"../node_modules/tinymce/tinymce.js",
	"../node_modules/tinymce/themes/modern/theme.js",
	"../node_modules/tinymce/plugins/link/plugin.js",
	"../node_modules/tinymce/plugins/paste/plugin.js",
	"../node_modules/tinymce/plugins/table/plugin.js",
	"../node_modules/tinymce/plugins/advlist/plugin.js",
	"../node_modules/tinymce/plugins/autoresize/plugin.js",
	"../node_modules/tinymce/plugins/lists/plugin.js",
	"../node_modules/tinymce/plugins/code/plugin.js"
]

Import `TinymceModule` in you `app.module.ts`:
```typescript
import { TinymceModule } from 'angular2-tinymce';

@NgModule({
	imports: [
		...
		TinymceModule
	],
	...
})
export class AppModule { }
```

Then use it:
```html
<app-tinymce [formControl]='contentControl'></app-tinymce>
```
or
```html
<app-tinymce [(ngModel)]='content'></app-tinymce>
```

## Configure
You can configure TinyMCE globally:
```typescript
import { TinymceModule } from 'angular2-tinymce';

@NgModule({
	imports: [
		...
		TinymceModule.withConfig({
			...  //any TinyMCE config here
		})
	],
	...
})
export class AppModule { }
```
Please note that config is extended a bit.

- Besides the original config angular2-tinymce supports `baseURL` for providing, i.e., custom plugins paths.

- `auto_focus` option is boolean instead of string.
- You cannot specify `selector` option (and you don't need to, right?).
- `setup` and `init_instance_callback` are executed after the components'.
- You can view more info about supported options [here] (https://github.com/orosroman/ng2-tinymce-alt/blob/master/src/angular2-tinymce.config.interface.ts)