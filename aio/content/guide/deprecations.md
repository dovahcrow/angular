# Deprecated APIs and Features

Angular strives to balance innovation and stability.
Sometimes, APIs and features become obsolete and need to be removed or replaced so that Angular can stay current with new best practices, changing dependencies, or changes in the (web) platform itself.

To make these transitions as easy as possible, we deprecate APIs and features for a period of time before removing them. This gives you time to update your apps to the latest APIs and best practices.

This guide contains a summary of all Angular APIs and features that are currently deprecated.


<div class="alert is-helpful">


Features and APIs that were deprecated in v6 or earlier are candidates for removal in version 9 or any later major version. For information about Angular's deprecation and removal practices, see [Angular Release Practices](guide/releases#deprecation-practices "Angular Release Practices: Deprecation practices").

For step-by-step instructions on how to update to the latest Angular release, use the interactive update guide at [update.angular.io](https://update.angular.io).

</div>


## Index

To help you future-proof your apps, the following table lists all deprecated APIs and features, organized by the release in which they are candidates for removal. Each item is linked to the section later in this guide that describes the deprecation reason and replacement options.

<!--
deprecation -> removal cheat sheet
v4 - v7
v5 - v8
v6 - v9
v7 - v10
v8 - v11
-->


| Area | API or Feature | May be removed in |
| ---- | -------------- | ----------------- |
| `@angular/common` | [Pipes using Intl API](#i18n-pipes) | <!--v8--> v9 |
| `@angular/common` | [`ReflectiveInjector`](#reflectiveinjector) | <!--v8--> v9 |
| `@angular/core` | [`CollectionChangeRecord`](#core) | <!--v7--> v9 |
| `@angular/core` | [`DefaultIterableDiffer`](#core) | <!--v7--> v9 |
| `@angular/core` | [`ReflectiveKey`](#core) | <!--v8--> v9 |
| `@angular/core` | [`RenderComponentType`](#core) | <!--v7--> v9 |
| `@angular/core` | [`Renderer`](#core) | <!--v7--> v9 |
| `@angular/core` | [`RootRenderer`](#core) | <!--v7--> v9 |
| `@angular/core` | [`ViewEncapsulation.Native`](#core) | v9 |
| `@angular/forms` | [`ngForm` element selector](#ngform) | v9 |
| `@angular/forms` | [`NgFormSelectorWarning`](#forms) | v9 |
| `@angular/forms` | [`ngModel` with reactive forms](#ngmodel-reactive) | v9 |
| `@angular/router` | [`preserveQueryParams`](#router) | <!--v7--> v9 |
| `@angular/upgrade` | [`@angular/upgrade`](#upgrade) | <!--v8--> v9 |
| `@angular/upgrade` | [`getAngularLib`](#upgrade-static) | <!--v8--> v9 |
| `@angular/upgrade` | [`setAngularLib`](#upgrade-static) | <!--v8--> v9 |
| template syntax | [`/deep/`, `>>>`, and `::ng-deep`](#deep-component-style-selector) | <!--v7--> v9 |
| template syntax | [`<template`>](#template-tag) | <!--v7--> v9 |
| service worker | [`versionedFiles` setting](#sw-versionedfiles)| v9 |
| polyfills | [reflect-metadata](#reflect-metadata) | <!--v8--> v9 |
| `@angular/core` | [`defineInjectable`](#core) | v11 |
| `@angular/router` | [`loadChildren` string syntax](#loadChildren) | v11 |
| `@angular/router` | [`ActivatedRoute` params and `queryParams` properties](#activatedroute-props) | unspecified |




## Deprecated APIs

This section contains a complete list all of the currently-deprecated APIs, with details to help you plan your migration to a replacement.


<div class="alert is-helpful">

Tip: In the [API reference section](api) of this doc site, deprecated APIs are indicated by ~~strikethrough.~~ You can filter the API list by [**Status: deprecated**](api?status=deprecated).

</div>



{@a common}
### @angular/common


| API | Replacement | Deprecation announced | Notes |
| --- | ----------- | --------------------- | ----- |
| [`DeprecatedI18NPipesModule`](api/common/DeprecatedI18NPipesModule) | [`CommonModule`](api/common/CommonModule#pipes) | v5 | See [Pipes](#i18n-pipes) |
 | [`DeprecatedCurrencyPipe`](api/common/DeprecatedCurrencyPipe) | [`CurrencyPipe`](api/common/CurrencyPipe) | v5  | See [Pipes](#i18n-pipes) |
 | [`DeprecatedDatePipe`](api/common/DeprecatedDatePipe) | [`DatePipe`](api/common/DatePipe) | v5  | See [Pipes](#i18n-pipes) |
 | [`DeprecatedDecimalPipe`](api/common/DeprecatedDecimalPipe) | [`DecimalPipe`](api/common/DecimalPipe) | v5  | See [Pipes](#i18n-pipes) |
 | [`DeprecatedPercentPipe`](api/common/DeprecatedPercentPipe) | [`PercentPipe`](api/common/PercentPipe) | v5 | See [Pipes](#i18n-pipes) |


{@a core}
### @angular/core

| API | Replacement | Deprecation announced | Notes |
| --- | ----------- | --------------------- | ----- |
| [`CollectionChangeRecord`](api/core/CollectionChangeRecord) | [`IterableChangeRecord`](api/core/IterableChangeRecord) | v4 | none |
| [`DefaultIterableDiffer`](api/core/DefaultIterableDiffer) | n/a | v4 | Not part of public API. |
| [`defineInjectable`](api/core/defineInjectable) | `ɵɵdefineInjectable` | v8 | Used only in generated code. No source code should depend on this API. |
| [`ReflectiveInjector`](api/core/ReflectiveInjector) | [`Injector.create`](api/core/Injector#create)  | v5 | See [`ReflectiveInjector`](#reflectiveinjector) |
| [`ReflectiveKey`](api/core/ReflectiveKey) | none | v5 | none |
| [`RenderComponentType`](api/core/RenderComponentType) | [`RendererType2`](api/core/RendererType2) and  [`Renderer2`](api/core/Renderer2) | v4 | none |
| [`Renderer`](api/core/Renderer) | [`Renderer2`](api/core/Renderer2) | v4 | none |
| [`RootRenderer`](api/core/RootRenderer) | [`RendererFactory2`](api/core/RendererFactory2) | v4 | none |
| [`ViewEncapsulation.Native`](api/core/ViewEncapsulation#Native) | [`ViewEncapsulation.ShadowDom`](api/core/ViewEncapsulation#ShadowDom) | v6 | Use the native encapsulation mechanism of the renderer. See [view.ts](https://github.com/angular/angular/blob/3e992e18ebf51d6036818f26c3d77b52d3ec48eb/packages/core/src/metadata/view.ts#L32).


{@a forms}
### @angular/forms

| API | Replacement | Deprecation announced | Notes |
| --- | ----------- | --------------------- | ----- |
| [`NgFormSelectorWarning`](api/forms/NgFormSelectorWarning) | n/a | v6 | See [ngForm](#ngform). |

{@a router}
### @angular/router

| API | Replacement | Deprecation announced | Notes |
| --- | ----------- | --------------------- | ----- |
| [`preserveQueryParams`](api/router/NavigationExtras#preserveQueryParams) | [`queryParamsHandling`](api/router/NavigationExtras#queryParamsHandling) | v4 | none |


{@a upgrade}
### @angular/upgrade

| API | Replacement | Deprecation announced | Notes |
| --- | ----------- | --------------------- | ----- |
| [All entry points](api/upgrade) | [`@angular/upgrade/static`](api/upgrade/static) | v5 | See [Upgrading from AngularJS](guide/upgrade). |

{@a upgrade-static}
### @angular/upgrade/static

| API | Replacement | Deprecation announced | Notes |
| --- | ----------- | --------------------- | ----- |
| [`getAngularLib`](api/upgrade/static/getAngularLib) | [`getAngularJSGlobal`](api/upgrade/static/getAngularJSGlobal) | v5 | See [Upgrading from AngularJS](guide/upgrade). |
[`setAngularLib`](api/upgrade/static/setAngularLib) | [`setAngularJSGlobal`](api/upgrade/static/setAngularJSGlobal) | v5 | See [Upgrading from AngularJS](guide/upgrade). |



{@a deprecated-features}
## Deprecated features

This section lists all of the currently-deprecated features, which includes template syntax, configuration options, and any other deprecations not listed in the [Deprecated APIs](#deprecated-apis) section above. It also includes deprecated API usage scenarios or API combinations, to augment the information above.



{@a deep-component-style-selector}
### `/deep/`, `>>>` and `:ng-deep` component style selectors

The shadow-dom-piercing descendant combinator is deprecated and support is being [removed from major browsers and tools](https://developers.google.com/web/updates/2017/10/remove-shadow-piercing). As such, in v4 we deprecated support in Angular for all 3 of `/deep/`, `>>>` and `::ng-deep`. Until removal, `::ng-deep` is preferred for broader compatibility with the tools.

For more information, see [/deep/, >>>, and ::ng-deep](guide/component-styles#deprecated-deep--and-ng-deep "Component Styles guide, Deprecated deep and ngdeep")
 in the Component Styles guide.


{@a template-tag}
### &lt;template&gt; tag

The `<template>` tag was deprecated in v4 to avoid colliding with the DOM's element of the same name (such as when using web components). Use `<ng-template>` instead. For more information, see the [Ahead-of-Time Compilation](guide/aot-compiler#enablelegacytemplate) guide.



{@a ngform}
### ngForm element selector

Support for using `ngForm` element selector was deprecated in v6.
It has been deprecated to be consistent with other core Angular selectors, which are typically written in kebab-case.

Deprecated:

```
<ngForm #myForm="ngForm">
```

Replacement:

```
<ng-form #myForm="ngForm">
```

The [`NgFormSelectorWarning`](api/forms/NgFormSelectorWarning) directive is solely used to display warnings when the deprecated `ngForm` selector is used.


{@a ngmodel-reactive}
### ngModel with reactive forms

Support for using the `ngModel` input property and `ngModelChange` event with reactive form directives was deprecated in version 6.

For more information, see the usage notes for [`FormControlDirective`](api/forms/FormControlDirective#use-with-ngmodel) and [`FormControlName`](api/forms/FormControlName#use-with-ngmodel).


{@a sw-versionedfiles}
### Service worker versionedFiles

In the service worker configuration file `ngsw-config.json`, `versionedFiles` and `files` have the same behavior. As of v6, `versionedFiles` is deprecated; use `files` instead.

For more information, see [Service Worker Configuration](guide/service-worker-config#assetgroups).


{@a reflectiveinjector}
### ReflectiveInjector

In v5, Angular replaced the `ReflectiveInjector` with the `StaticInjector`. The injector no longer requires the Reflect polyfill, reducing application size for most developers.

Before:

```
ReflectiveInjector.resolveAndCreate(providers);
```

After:

```
Injector.create({providers});
```

{@a i18n-pipes}
### Pipes using Intl API

<!--
From https://blog.angular.io/version-5-0-0-of-angular-now-available-37e414935ced
-->

Angular used to rely on the browser to provide number, date, and currency formatting using browser i18n APIs. This practice meant that most apps needed to use a polyfill, users were seeing inconsistent results across browsers, and common formats (such as the currency pipe) didn’t match developer expectations out of the box.

In version 4.3, Angular introduced new number, date, and currency pipes that increase standardization across browsers and eliminate the need for i18n polyfills. These pipes use the Unicode Common Locale Data Repository (CLDR) instead of the JS Intl API to provide extensive locale support.

In version 5.0.0, Angular updated its standard pipes to use the CLRD implementation.
At that time, Angular also added [`DeprecatedI18NPipesModule`](api/common/DeprecatedI18NPipesModule) and related APIs to provide limited-time access to the old behavior. If you need to use these `Deprecated*` pipes, see [Angular change log](https://github.com/angular/angular/blob/master/CHANGELOG.md#i18n-pipes) and the [Date Formats mappings](https://docs.google.com/spreadsheets/d/12iygt-_cakNP1VO7MV9g4lq9NsxVWG4tSfc98HpHb0k/edit#gid=0 "Date Formats Google sheet").

Reminder: If you use these `Deprecated*` pipes, you should migrate to the current APIs listed above as soon as possible. These deprecated APIs are candidates for removal in version 9.


{@a loadChildren}
### loadChildren string syntax

When Angular first introduced lazy routes, there wasn't browser support for dynamically loading additional JavaScript. Angular created our own scheme using the syntax `loadChildren: './lazy/lazy.module#LazyModule'` and built tooling to support it. Now that ECMAScript dynamic import is supported in many browsers, Angular is moving toward this new syntax.

In v8, the string syntax for the [`loadChildren`](api/router/LoadChildren) route specification was deprecated, in favor of new syntax that uses `import()` syntax.

Before:

```
const routes: Routes = [{
  path: 'lazy',
  // The following string syntax for loadChildren is deprecated
  loadChildren: './lazy/lazy.module#LazyModule'
}];
```

After:

```
const routes: Routes = [{
  path: 'lazy',
  // The new import() syntax
  loadChildren: () => import('./lazy/lazy.module').then(m => m.LazyModule)
}];
```


<div class="alert is-helpful">


**v8 update**: When you update to version 8, the [`ng update`](cli/update) command performs the transformation automatically. Prior to version 7, the `import()` syntax only works in JIT mode (with view engine).


</div>



{@a activatedroute-props}
### ActivatedRoute params and queryParams properties

[ActivatedRoute](api/router/ActivatedRoute) contains two [properties](api/router/ActivatedRoute#properties) that are less capable than their replacements and may be deprecated in a future Angular version.

| Property | Replacement |
| -------- | ----------- |
| `params` | `paramMap` |
| `queryParams` | `queryParamMap` |

For more information see the [Router guide](guide/router#activated-route).


{@a reflect-metadata}
### Dependency on a reflect-metadata polyfill in JIT mode
Angular applications, and specifically applications that relied on the JIT compiler, used to require a polyfill for the [reflect-metadata](https://github.com/rbuckton/reflect-metadata) APIs.

The need for this polyfill was removed in Angular version 8.0 ([see #14473](https://github.com/angular/angular-cli/pull/14473)), rendering the presence of the poylfill in most Angular applications unnecessary. Because the polyfill can be depended on by 3rd-party libraries, instead of removing it from all Angular projects, we are deprecating the requirement for this polyfill as of version 8.0. This should give library authors and application developers sufficient time to evaluate if they need the polyfill, and perform any refactoring necessary to remove the dependency on it.

In typical Angular project, the polyfill is not used in production builds, so deprecating it (rather than removing it)  doesn't have impact on the production applications. The goal behind this removal is overall simplification of the build setup and decrease in the number of external dependencies.

We expect to remove the polyfill from most if not all CLI projects via an `ng upgrade` migration from version 8 to 9.


{@a removed}
## Removed APIs

The following APIs have been removed starting with version 8.0.0:

| Package | API            | Replacement | Notes |
| ------- | -------------- | ----------- | ----- |
| [`@angular/http`](https://v7.angular.io/api/http) | All exports | [`@angular/common/http`](https://v7.angular.io/api/common/http) | See [below](#http). |
[`@angular/http/testing`](https://v7.angular.io/api/http/testing) | All exports | [`@angular/common/http/testing`](https://v7.angular.io/api/common/http/testing) | See [below](#http). |
| `@angular/platform-browser` | [`DOCUMENT`](https://v7.angular.io/api/platform-browser/DOCUMENT) | [`DOCUMENT` in `@angular/common`](https://v7.angular.io/api/common/DOCUMENT) | Updating to version 8 with [`ng update`](cli/update) changes this automatically.  |
| `@angular/core/testing` | [`TestBed.deprecatedOverrideProvider()`](https://v7.angular.io/api/core/testing/TestBed#deprecatedoverrideprovider) | [`TestBed.overrideProvider()`] (api/core/testing/TestBed#overrideprovider) | none |
| `@angular/core/testing` | [`TestBedStatic.deprecatedOverrideProvider()`](https://v7.angular.io/api/core/testing/TestBedStatic#deprecatedoverrideprovider) | [`TestBedStatic.overrideProvider()`](api/core/testing/TestBedStatic#overrideprovider) | none |



<!-- The following anchor is used by redirects from the removed API pages. Do not change or remove. -->
{@a http}
### @angular/http

<!--
Deprecation announced in version 5
https://blog.angular.io/version-5-0-0-of-angular-now-available-37e414935ced)
-->


The entire [`@angular/http`](http://v7.angular.io/api/http) package has been removed. Use [`@angular/common/http`](api/common/http) instead.

The new API is a smaller, easier, and more powerful way to make HTTP requests in Angular.
The new API simplifies the default ergonomics: There is no need to map by invoking the `.json()` method.
It also supports typed return values and interceptors.

To update your apps:
* Replace `HttpModule` with [`HttpClientModule`](api/common/http/HttpClientModule) (from [`@angular/common/http`](api/common/http)) in each of your modules.
* Replace the `Http` service with the [`HttpClient`](api/common/http/HttpClient) service.
* Remove any `map(res => res.json())` calls. They are no longer needed.

For more information about using `@angular/common/http`, see the [HttpClient guide](guide/http "HTTP Client guide").


| `@angular/http` | Closest replacement in `@angular/common/http` |
| ------------- | ------------------------------------------- |
| `BaseRequestOptions` |  [`HttpRequest`](/api/common/http/HttpRequest) |
| `BaseResponseOptions` | [`HttpResponse`](/api/common/http/HttpResponse) |
| `BrowserXhr` |  |
| `Connection` | [`HttpBackend`](/api/common/http/HttpBackend) |
| `ConnectionBackend` | [`HttpBackend`](/api/common/http/HttpBackend) |
| `CookieXSRFStrategy` | [`HttpClientXsrfModule`](/api/common/http/HttpClientXsrfModule) |
| `Headers` | [`HttpHeaders`](/api/common/http/HttpHeaders) |
| `Http` | [`HttpClient`](/api/common/http/HttpClient) |
| `HttpModule` | [`HttpClientModule`](/api/common/http/HttpClientModule) |
| `Jsonp` | [`HttpClient`](/api/common/http/HttpClient) |
| `JSONPBackend` | [`JsonpClientBackend`](/api/common/http/JsonpClientBackend) |
| `JSONPConnection` | [`JsonpClientBackend`](/api/common/http/JsonpClientBackend) |
| `JsonpModule` | [`HttpClientJsonpModule`](/api/common/http/HttpClientJsonpModule) |
| `QueryEncoder` | [`HttpUrlEncodingCodec`](/api/common/http/HttpUrlEncodingCodec) |
| `ReadyState` | [`HttpBackend`](/api/common/http/HttpBackend) |
| `Request` | [`HttpRequest`](/api/common/http/HttpRequest) |
| `RequestMethod` | [`HttpClient`](/api/common/http/HttpClient) |
| `RequestOptions` | [`HttpRequest`](/api/common/http/HttpRequest) |
| `RequestOptionsArgs` | [`HttpRequest`](/api/common/http/HttpRequest) |
| `Response` | [`HttpResponse`](/api/common/http/HttpResponse) |
| `ResponseContentType` | [`HttpClient`](/api/common/http/HttpClient) |
| `ResponseOptions` | [`HttpResponse`](/api/common/http/HttpResponse) |
| `ResponseOptionsArgs` | [`HttpResponse`](/api/common/http/HttpResponse) |
| `ResponseType` | [`HttpClient`](/api/common/http/HttpClient) |
| `URLSearchParams` | [`HttpParams`](/api/common/http/HttpParams) |
| `XHRBackend` | [`HttpXhrBackend`](/api/common/http/HttpXhrBackend) |
| `XHRConnection` | [`HttpXhrBackend`](/api/common/http/HttpXhrBackend) |
| `XSRFStrategy` | [`HttpClientXsrfModule`](/api/common/http/HttpClientXsrfModule) |


| `@angular/http/testing` | Closest replacement in `@angular/common/http/testing` |
| --------------------- | ------------------------------------------- |
| `MockBackend` | [`HttpTestingController`](/api/common/http/testing/HttpTestingController) |
| `MockConnection` | [`HttpTestingController`](/api/common/http/testing/HttpTestingController) |

