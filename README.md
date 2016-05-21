# bootstrap-breakpointify
Fight "class creep" by adding breakpoint suffixes to [Bootstrap v4's utility classes][utils].

For example, `.m-a-1-gt-md`:
- applies Bootstrap's "size 1" margin to all sides (the `m-a-1` Bootstrap class)
- at Bootstrap breakpoints greater than medium (`gt-md`).

## Purpose

As a web project grows – and particularly as new contributors begin making changes to CSS – it's common for simple utilities to be used and re-used in dozens of ways. Without using "breakpointified" utilities, each usage tends to add both to the project weight and to the difficulty of grokking the entirety of the project's CSS.

Especially when "one-use" classes are repeatedly developed (eg: when a website contains multiple very unique landing pages), many projects tend to grow a base of "write-only CSS" (becuase editing "old" CSS is tedious and requires good visual testing).

Using "breakpointified" utilities can help slow this "class creep" in your projects.

## Install

```bash
bower install bootstrap-breakpointify
```

Note: this library must be `@import`ed after bootstrap, as it requires [Bootstrap's responsive breakpoint mixins][mixins].

```scss
@import '../bower_components/bootstrap/scss/bootstrap';
@import '../bower_components/bootstrap-breakpointify/all';
```

## Usage
Breakpoint suffixes are appended to the end of the normal classes. See the [bootstrap docs][utils] for more information. All suffixes begin with either `gt` ("greater than") or `lt` ("less than").

### "Greater-than" suffixes
"Greater-than" suffixes apply the class at the following [Bootstrap breakpoints][mixins].

suffix  | x-small | small | medium | large | x-large
:-----: | :-----: | :---: | :----: | :---: | :-----:
`gt-xs` |         | ✓     | ✓      | ✓     | ✓
`gt-sm` |         |       | ✓      | ✓     | ✓
`gt-md` |         |       |        | ✓     | ✓
`gt-lg` |         |       |        |       | ✓

### "Less-than" suffixes
"Less-than" suffixes apply the class at the following [Bootstrap breakpoints][mixins].

suffix  | x-small | small | medium | large | x-large
:-----: | :-----: | :---: | :----: | :---: | :-----:
`lt-sm` | ✓       |       |        |       |
`lt-md` | ✓       | ✓     |        |       |
`lt-lg` | ✓       | ✓     | ✓      |       |
`lt-xl` | ✓       | ✓     | ✓      | ✓     |

### Available Prefixes

This library "breakpointifies" all of Bootstrap's [utility clases][utils].

#### Properties – First Character

- m – `margin`
- p - `padding`

#### Direction(s) – Second Character

- t - `top`
- r - `right`
- b - `bottom`
- l - `left`
- x - `x-axis` (both `left` and `right`)
- y - `y-axis` (both `top` and `bottom`)
- a – `all` (all of the above: `top`, `right`, `bottom`, and `left`)

#### Size – Third Character

- 0 – `none`
- 1 – `normal` (the relevant Bootstrap `$spacer` value)
- 2 – `size 2` (the relevant Bootstrap "size 2" value – by default, `$spacer * 1.5`)
- 3 – `size 3` (the relevant Bootstrap "size 3" value – by default, `$spacer * 3`)

### Examples
- `m-a-0-gt-lg` – `margin` `all` `size 0` `greater than` `large` – remove margin from all sides at breakpoints greater than Bootstrap's large (`lg`) breakpoint.
- `m-b-3-gt-md` – `margin` `bottom` `size 3` `greater than` `medium` – apply "size 3" margin-bottom at breakpoints greater than Bootstrap's medium (`md`) breakpoint.
- `p-t-1-lt-md` – `padding` `top` `size 1` `less than` `medium` – apply normal padding-top at breakpoints less than Bootstrap's medium (`md`) breakpoint.

## What about unused CSS classes?
You could use [UnCSS](https://github.com/giakki/uncss) to programmatically remove unused CSS, but it's likely not worth the savings.

Browser rendering performance is not impacted by unused CSS classes, and this entire library adds the equivalent of a small icon to your page weight. Ensure your stylesheets are served with gzip compression for best optimization.

[utils]: http://v4-alpha.getbootstrap.com/components/utilities/#spacing
[mixins]: http://v4-alpha.getbootstrap.com/layout/overview/#responsive-breakpoints
