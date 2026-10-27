---
kanon:
  description: "Bulma edit/create form with inline validation, loading state, and htmx swap"
  keywords:
    - bulma
    - form
    - htmx
    - hyperscript
    - validation
    - errors
    - hx-preserve
    - loading
---
```html
<form hx-post="/items/new" hx-swap="outerHTML" hx-select="form" class="box"
    _="
       on htmx:beforeRequest toggle .is-loading on the first <button.is-primary/> in me end
       on htmx:afterRequest toggle .is-loading on the first <button.is-primary/> in me end
    ">
    <div class="field">
        <label class="label">Name</label>
        <div class="control">
            <input id="item-name" name="name" class="input" type="text"
                placeholder="My Item" value="{{ item.name if item }}" hx-preserve>
        </div>
        {% if "name" in errors %}
        <p class="help is-danger">{{ errors.name }}</p>
        {% endif %}
    </div>
    <div class="field">
        <label class="label">Quantity</label>
        <div class="control">
            <div class="field has-addons">
                <div class="control">
                    <input id="item-qty" name="qty" class="input" type="number"
                        placeholder="0" value="{{ item.qty if item }}" hx-preserve>
                </div>
                <div class="control">
                    <p class="button is-static">kg</p>
                </div>
            </div>
        </div>
        {% if "qty" in errors %}
        <p class="help is-danger">{{ errors.qty }}</p>
        {% endif %}
    </div>
    <div class="field">
        <label class="label">Notes</label>
        <div class="control">
            <textarea id="item-notes" name="notes" class="textarea" hx-preserve>{{ item.notes if item }}</textarea>
        </div>
        {% if "notes" in errors %}
        <p class="help is-danger">{{ errors.notes }}</p>
        {% endif %}
    </div>
    <div class="field is-grouped">
        <div class="control">
            <div class="buttons">
                <button class="button is-primary">Save</button>
                <a class="button" href="/items" hx-boost="true">Return</a>
            </div>
        </div>
    </div>
    {% if message %}
    <p class="help" _="on load wait 1s then remove me">{{ message.text }}</p>
    {% endif %}
</form>
```

**Placeholders:** Action URL (`hx-post`/`hx-put`), field `name`/`id` attributes, placeholder text, value expressions, addon unit label, `href` for Return button.

**Notes:** `hx-swap="outerHTML" hx-select="form"` means the server re-renders the same form (with errors populated) on a `400` and htmx replaces it in place — no page navigation, errors appear inline inside each `.field`. Use `hx-post` for create and `hx-put` for edit; the rest of the form is identical. `hx-preserve` on an input keeps its current DOM value unchanged across swaps — requires a unique, stable `id`. The loading hyperscript toggles `.is-loading` on the primary button for the duration of the request. The flash message removes itself after 1 second via hyperscript.

**Addon fields:** Use `div.field.has-addons` with `div.control` children — one for the `input.input` and one for `p.button.is-static` holding the unit or suffix label. Keep the addon wrapper inside the outer `.field`'s `.control` div so the error `p.help` sits at `.field` level and spans the full width.

**Horizontal layout:** Wrap any field in `div.field.is-horizontal` with `div.field-label.is-normal > label.label` and `div.field-body > div.field` as children to get a left-label, right-input layout. Useful for dense data-entry forms.

**Timezone input:** To capture the browser timezone, add `<input type="hidden" name="tz" id="tz-input" value="Etc/UTC">` and append `on load set #tz-input's value to Intl.DateTimeFormat().resolvedOptions().timeZone end` to the form's hyperscript.
