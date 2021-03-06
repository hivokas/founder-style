---
extends: _layouts.master
section: content
title: Validation
previousLink: /views
previous: Views
nextLink: /eloquent
next: Eloquent
---

When referencing validation rules, you must always use the array syntax, rather than pipe-delimited strings.

This ensures consistent formatting whether you have one or many validation rules, if you use the `Rule` class, or if your rules are complex enough such that you need to create [custom validation rules](https://laravel.com/docs/5.5/validation#custom-validation-rules).

```php
// Good
request()->validate([
    'name' => ['required'],
    'email' => ['required', Rule::exists('users')],
]);

// Bad
request()->validate([
    'name' => 'required',
    'email' => ['required', Rule::exists('users')],
]);
```

## Simple custom validation rules <a class="text-grey" name="simple-custom-validation-rules" href="#simple-custom-validation-rules">#</a>

When declaring simple validation rules, always use `snake_case` per the Laravel framework convention.

```php
Validator::extend('phone_number', function ($attribute, $value) {
    return PhoneNumber::isValid($value);
});
```
