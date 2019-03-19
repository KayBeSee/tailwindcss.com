---
extends: _layouts.documentation
title: "Position"
description: "Utilities for controlling how an element is positioned in the DOM."
features:
  responsive: true
  customizable: false
  hover: false
  focus: false
---

@include('_partials.class-table', [
  'rows' => [
    [
      '.static',
      "position: static;",
      "Position an element according to the normal flow of the document.",
    ],
    [
      '.fixed',
      "position: fixed;",
      "Position an element relative to the browser window.",
    ],
    [
      '.absolute',
      "position: absolute;",
      "Position an element outside of the normal flow of the document, causing neighboring elements to act as if the element doesn't exist.",
    ],
    [
      '.relative',
      "position: relative;",
      "Position an element according to the normal flow of the document.",
    ],
    [
      '.sticky',
      "position: sticky;",
      "Position an element relatively until its containing block crosses a specified threshold, then position it relative to the viewport.",
    ],
    [
      '.top-0',
      "top: 0;",
      "Anchor absolutely positioned element to the top edge of the nearest positioned parent.",
    ],
    [
      '.right-0',
      "right: 0;",
      "Anchor absolutely positioned element to the right edge of the nearest positioned parent.",
    ],
    [
      '.bottom-0',
      "bottom: 0;",
      "Anchor absolutely positioned element to the bottom edge of the nearest positioned parent.",
    ],
    [
      '.left-0',
      "left: 0;",
      "Anchor absolutely positioned element to the left edge of the nearest positioned parent.",
    ],
    [
      '.inset-y-0',
      "top: 0;\nbottom: 0;",
      "Anchor absolutely positioned element to the top and bottom edges of the nearest positioned parent.",
    ],
    [
      '.inset-x-0',
      "right: 0;\nleft: 0;",
      "Anchor absolutely positioned element to the left and right edges of the nearest positioned parent.",
    ],
    [
      '.inset-0',
      "top: 0;\nright: 0;\nbottom: 0;\nleft: 0;",
      "Anchor absolutely positioned element to all the edges of the nearest positioned parent.",
    ],
    [
      '.inset-auto',
      "top: auto;\nright: auto;\nbottom: auto;\nleft: auto;",
      "Reset absolutely positioned element to all the edges from a given breakpoint onwards.",
    ],
    [
      '.top-auto',
      "top: auto;",
      "Reset absolutely positioned element to the top edge",
    ],
    [
      '.bottom-auto',
      "bottom: auto;",
      "Reset absolutely positioned element to the bottom edge",
    ],
    [
      '.left-auto',
      "left: auto;",
      "Reset absolutely positioned element to the left edge",
    ],
    [
      '.right-auto',
      "right: auto;",
      "Reset absolutely positioned element to the right edge",
    ],
    [
      '.inset-y-auto',
      "top: auto;\nbottom: auto;",
      "Reset absolutely positioned element to the top and bottom edge",
    ],
    [
      '.inset-x-auto',
      "left: auto;\nright: auto;",
      "Reset absolutely positioned element to the left and right edge",
    ],
  ]
])

## Static <span class="ml-2 font-semibold text-gray-600 text-sm uppercase tracking-wide">Default</span>

Use `.static` to position an element according to the normal flow of the document.

Any offsets will be ignored and the element will not act as a position reference for absolutely positioned children.

@component('_partials.code-sample')
<div class="relative bg-gray-400 p-4">
  <div class="static h-32 bg-gray-600 p-4 text-gray-900">
    <p>Static parent</p>
    <div class="absolute bottom-0 left-0 bg-gray-800 p-4 text-gray-400">
      <p>Absolute child</p>
    </div>
  </div>
</div>

@slot('code')
<div class="static bg-gray-600">
  Static parent
  <div class="absolute bottom-0 left-0 bg-gray-800">
    Absolute child
  </div>
</div>
@endslot
@endcomponent

## Relative

Use `.relative` to position an element according to the normal flow of the document.

Offsets are calculated relative to the element's normal position and the element *will* act as a position reference for absolutely positioned children.

@component('_partials.code-sample')
<div class="relative bg-gray-400 p-4">
  <div class="relative h-32 bg-gray-600 p-4 text-gray-900">
    <p>Relative parent</p>
    <div class="absolute bottom-0 left-0 bg-gray-800 p-4 text-gray-400">
      <p>Absolute child</p>
    </div>
  </div>
</div>

@slot('code')
<div class="relative bg-gray-600">
  Relative parent
  <div class="absolute bottom-0 left-0 bg-gray-800">
    Absolute child
  </div>
</div>
@endslot
@endcomponent

## Absolute

Use `.absolute` to position an element *outside* of the normal flow of the document, causing neighboring elements to act as if the element doesn't exist.

Offsets are calculated relative to the nearest parent that has a position other than `static`, and the element *will* act as a position reference for other absolutely positioned children.

@component('_partials.code-sample')

<p class="text-sm text-gray-600 mb-1">With static positioning</p>
<div class="relative bg-gray-400 px-4 pt-2 pb-4 mb-6">
  <p class="mb-2 text-gray-700">Relative parent</p>
  <div class="static bg-gray-500 p-4 text-gray-700">
    <p class="mb-2">Static parent</p>
    <div class="static bottom-0 left-0 bg-gray-800 p-4 text-gray-400 inline-block">
      <p>Static child</p>
    </div>
    <div class="bg-gray-400 p-4 text-gray-700 inline-block">
      <p>Static sibling</p>
    </div>
  </div>
</div>

<p class="text-sm text-gray-600 mb-1">With absolute positioning</p>
<div class="relative bg-gray-400 px-4 pt-2 pb-4">
  <p class="mb-2 text-gray-700">Relative parent</p>
  <div class="static bg-gray-500 p-4 text-gray-700">
    <p class="mb-2">Static parent</p>
    <div class="absolute top-0 right-0 bg-gray-800 p-4 text-gray-400 inline-block">
      <p>Absolute child</p>
    </div>
    <div class="bg-gray-400 p-4  text-gray-700 inline-block">
      <p>Static sibling</p>
    </div>
  </div>
</div>

@slot('code')
<div class="relative bg-gray-400">
  Relative parent
  <div class="static bg-gray-600">
    Static parent
    <div class="absolute top-0 right-0 bg-gray-800">
      Absolute child
    </div>
    <div class="bg-gray-400 inline-block">
      Static sibling
    </div>
  </div>
</div>
@endslot
@endcomponent

## Fixed

Use `.fixed` to position an element relative to the browser window.

Offsets are calculated relative to the viewport and the element *will* act as a position reference for absolutely positioned children.

@component('_partials.code-sample')
<div class="rounded-b overflow-hidden max-w-md mx-auto mt-4 mb-4">
  <div class="rounded-t border-t border-l border-r border-grey-light bg-gray-200 flex px-4 py-3">
    <div class="mr-6">
      <span class="inline-block rounded-full bg-gray-500 h-3 w-3 mr-1"></span>
      <span class="inline-block rounded-full bg-gray-500 h-3 w-3 mr-1"></span>
      <span class="inline-block rounded-full bg-gray-500 h-3 w-3"></span>
    </div>
    <div class="flex-1 bg-white border border-grey-light rounded mr-4"></div>
  </div>
  <div class="relative bg-gray-400 h-64">

    <!-- Hey fellow nerd! Yes, we're using position absolute instead of position fixed in the demo; it's the best way we could come up with to demonstrate how position fixed works without totally jacking up the layout of the entire documentation site. Forgive us! 😄 -->

    <div class="absolute left-0 right-0 top-0 bg-gray-800 text-gray-400 z-10 px-4 py-3">
      Fixed child
      <div class="absolute top-0 bottom-0 right-0 px-4 py-3 bg-gray-500 text-gray-800">
        Absolute child
      </div>
    </div>
    <div class="absolute inset-0 overflow-auto pt-16 px-4 pb-4">
      <p class="mb-4">Scroll me!</p>
      <p class="mb-4">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi. Nulla quis sem at nibh elementum imperdiet. Duis sagittis ipsum. Praesent mauris. Fusce nec tellus sed augue semper porta. Mauris massa. Vestibulum lacinia arcu eget nulla. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Curabitur sodales ligula in libero. </p>
      <p class="mb-4">Sed dignissim lacinia nunc. Curabitur tortor. Pellentesque nibh. Aenean quam. In scelerisque sem at dolor. Maecenas mattis. Sed convallis tristique sem. Proin ut ligula vel nunc egestas porttitor. Morbi lectus risus, iaculis vel, suscipit quis, luctus non, massa. Fusce ac turpis quis ligula lacinia aliquet. Mauris ipsum. Nulla metus metus, ullamcorper vel, tincidunt sed, euismod in, nibh. Quisque volutpat condimentum velit. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. </p>
      <p class="mb-4">Nam nec ante. Sed lacinia, urna non tincidunt mattis, tortor neque adipiscing diam, a cursus ipsum ante quis turpis. Nulla facilisi. Ut fringilla. Suspendisse potenti. Nunc feugiat mi a tellus consequat imperdiet. Vestibulum sapien. Proin quam. Etiam ultrices. Suspendisse in justo eu magna luctus suscipit. Sed lectus. Integer euismod lacus luctus magna. </p>
      <p class="mb-4">Quisque cursus, metus vitae pharetra auctor, sem massa mattis sem, at interdum magna augue eget diam. Vestibulum ante ipsum primis in faucibus orci luctus et ultrices posuere cubilia Curae; Morbi lacinia molestie dui. Praesent blandit dolor. Sed non quam. In vel mi sit amet augue congue elementum. Morbi in ipsum sit amet pede facilisis laoreet. Donec lacus nunc, viverra nec, blandit vel, egestas et, augue. Vestibulum tincidunt malesuada tellus. Ut ultrices ultrices enim. Curabitur sit amet mauris. Morbi in dui quis est pulvinar ullamcorper. Nulla facilisi. </p>
      <p class="mb-4">Integer lacinia sollicitudin massa. Cras metus. Sed aliquet risus a tortor. Integer id quam. Morbi mi. Quisque nisl felis, venenatis tristique, dignissim in, ultrices sit amet, augue. Proin sodales libero eget ante. Nulla quam. Aenean laoreet. Vestibulum nisi lectus, commodo ac, facilisis ac, ultricies eu, pede. Ut orci risus, accumsan porttitor, cursus quis, aliquet eget, justo. Sed pretium blandit orci. Ut eu diam at pede suscipit sodales. Aenean lectus elit, fermentum non, convallis id, sagittis at, neque. </p>
      <p class="mb-4">Nullam mauris orci, aliquet et, iaculis et, viverra vitae, ligula. Nulla ut felis in purus aliquam imperdiet. Maecenas aliquet mollis lectus. Vivamus consectetuer risus et tortor. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi. Nulla quis sem at nibh elementum imperdiet. Duis sagittis ipsum. Praesent mauris. Fusce nec tellus sed augue semper porta. Mauris massa. </p>
      <p class="mb-4">Vestibulum lacinia arcu eget nulla. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Curabitur sodales ligula in libero. Sed dignissim lacinia nunc. Curabitur tortor. Pellentesque nibh. Aenean quam. In scelerisque sem at dolor. Maecenas mattis. Sed convallis tristique sem. Proin ut ligula vel nunc egestas porttitor. Morbi lectus risus, iaculis vel, suscipit quis, luctus non, massa. Fusce ac turpis quis ligula lacinia aliquet. </p>
      <p>Mauris ipsum. Nulla metus metus, ullamcorper vel, tincidunt sed, euismod in, nibh. Quisque volutpat condimentum velit. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Nam nec ante. Sed lacinia, urna non tincidunt mattis, tortor neque adipiscing diam, a cursus ipsum ante quis turpis. Nulla facilisi. Ut fringilla. Suspendisse potenti. Nunc feugiat mi a tellus consequat imperdiet. Vestibulum sapien. Proin quam. </p>
    </div>
  </div>
</div>

@slot('code')
<div class="bg-gray-400 pt-16">
  <div class="fixed bg-gray-600">
    Fixed child
    <div class="absolute top-0 right-0 bg-gray-800">
      Absolute child
    </div>
  </div>

  Scroll me!

  Lorem ipsum...
</div>
@endslot
@endcomponent

## Sticky

<div class="text-sm bg-blue-100 text-blue-700 font-semi-bold px-4 py-2 mb-4 rounded">
  <div class="flex items-center">
    <div class="mr-2">
      <svg class="block text-blue-400 h-5 w-5" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path fill-rule="evenodd" clip-rule="evenodd" d="M16.432 15C14.387 9.893 12 8.547 12 6V3h.5a.5.5 0 0 0 .5-.5v-1a.5.5 0 0 0-.5-.5h-5a.5.5 0 0 0-.5.5v1a.5.5 0 0 0 .5.5H8v3c0 2.547-2.387 3.893-4.432 9-.651 1.625-2.323 4 6.432 4s7.083-2.375 6.432-4zm-1.617 1.751c-.702.21-2.099.449-4.815.449s-4.113-.239-4.815-.449c-.249-.074-.346-.363-.258-.628.22-.67.635-1.828 1.411-3.121 1.896-3.159 3.863.497 5.5.497s1.188-1.561 1.824-.497a15.353 15.353 0 0 1 1.411 3.121c.088.265-.009.553-.258.628z"/></svg>
    </div>
    <div>
      <p class="font-semibold">Note that sticky positioning is not supported in IE11.</p>
    </div>
  </div>
</div>

Use `.sticky` to position an element as `relative` until it crosses a specified threshold, then treat it as fixed until its parent is off screen.

Offsets are calculated relative to the element's normal position and the element *will* act as a position reference for absolutely positioned children.


@component('_partials.code-sample')
<iframe class="h-64 w-full" src="/embeds/position-sticky/index.html" frameborder="0"></iframe>

@slot('code')
<div>
    <div class="sticky top-0 ...">Sticky Heading 1</div>
    <p class="py-4">Quisque cursus...</p>
</div>
<div>
    <div class="sticky top-0 ...">Sticky Heading 2</div>
    <p class="py-4">Integer lacinia...</p>
</div>
<div>
    <div class="sticky top-0 ...">Sticky Heading 3</div>
    <p class="py-4">Nullam mauris...</p>
</div>
<!-- etc. -->
@endslot
@endcomponent

## Pinning edges

Use the `.{top|right|bottom|left|inset}-{value}` utilities to anchor absolutely positioned elements against any of the edges of the nearest positioned parent.

Combined with Tailwind's [spacing utilities](/docs/spacing), you'll probably find that these are all you need to precisely control absolutely positioned elements.

<div class="flex items-start mt-8 text-sm leading-none mb-8">
  <div class="pr-12">
    <div class="mb-3 text-gray-700 uppercase">Class</div>
    <div><code class="inline-block my-1 mr-1 px-2 py-1 font-mono border rounded">top|right|bottom|left|inset</code></div>
  </div>
  <div class="pl-12 pr-12 border-l">
    <div class="mb-3 text-gray-700">
    <span class="uppercase">space</span>
  </div>
  <div><code class="inline-block my-1 mr-1 px-2 py-1 font-mono border rounded">0</code> 0</div>
  <div><code class="inline-block my-1 mr-1 px-2 py-1 font-mono border rounded">auto</code> auto</div>
  </div>
</div>

@component('_partials.code-sample')
<div class="flex justify-around mb-8">
  <div>
    <p class="text-center text-sm text-gray-600 mb-1">.inset-x-0.top-0</p>
    <div class="relative h-24 w-24 bg-gray-400">
      <div class="absolute inset-x-0 top-0 h-8 bg-gray-700"></div>
    </div>
  </div>
  <div>
    <p class="text-center text-sm text-gray-600 mb-1">.inset-y-0.right-0</p>
    <div class="relative h-24 w-24 bg-gray-400">
      <div class="absolute inset-y-0 right-0 w-8 bg-gray-700"></div>
    </div>
  </div>
  <div>
    <p class="text-center text-sm text-gray-600 mb-1">.inset-x-0.bottom-0</p>
    <div class="relative h-24 w-24 bg-gray-400">
      <div class="absolute inset-x-0 bottom-0 h-8 bg-gray-700"></div>
    </div>
  </div>
  <div>
    <p class="text-center text-sm text-gray-600 mb-1">.inset-y-0.left-0</p>
    <div class="relative h-24 w-24 bg-gray-400">
      <div class="absolute inset-y-0 left-0 w-8 bg-gray-700"></div>
    </div>
  </div>
  <div>
    <p class="text-center text-sm text-gray-600 mb-1">.inset-0</p>
    <div class="relative h-24 w-24 bg-gray-400">
      <div class="absolute inset-0 bg-gray-700"></div>
    </div>
  </div>
</div>
<div class="flex justify-around">
  <div>
    <p class="text-center text-sm text-gray-600 mb-1">.left-0.top-0</p>
    <div class="relative h-24 w-24 bg-gray-400">
      <div class="absolute left-0 top-0 h-8 w-8 bg-gray-700"></div>
    </div>
  </div>
  <div>
    <p class="text-center text-sm text-gray-600 mb-1">.top-0.right-0</p>
    <div class="relative h-24 w-24 bg-gray-400">
      <div class="absolute top-0 right-0 h-8 w-8 bg-gray-700"></div>
    </div>
  </div>
  <div>
    <p class="text-center text-sm text-gray-600 mb-1">.right-0.bottom-0</p>
    <div class="relative h-24 w-24 bg-gray-400">
      <div class="absolute right-0 bottom-0 h-8 w-8 bg-gray-700"></div>
    </div>
  </div>
  <div>
    <p class="text-center text-sm text-gray-600 mb-1">.bottom-0.left-0</p>
    <div class="relative h-24 w-24 bg-gray-400">
      <div class="absolute bottom-0 left-0 h-8 w-8 bg-gray-700"></div>
    </div>
  </div>
  <div class="relative h-24 w-24 opacity-0"></div>
</div>

@slot('code')
<!-- Span top edge -->
<div class="relative h-24 w-24 bg-gray-400">
  <div class="absolute inset-x-0 top-0 h-8 bg-gray-700"></div>
</div>

<!-- Span right edge -->
<div class="relative h-24 w-24 bg-gray-400">
  <div class="absolute inset-y-0 right-0 w-8 bg-gray-700"></div>
</div>

<!-- Span bottom edge -->
<div class="relative h-24 w-24 bg-gray-400">
  <div class="absolute inset-x-0 bottom-0 h-8 bg-gray-700"></div>
</div>

<!-- Span left edge -->
<div class="relative h-24 w-24 bg-gray-400">
  <div class="absolute inset-y-0 left-0 bg-gray-700"></div>
</div>

<!-- Fill entire parent -->
<div class="relative h-24 w-24 bg-gray-400">
  <div class="absolute inset-0 bg-gray-700"></div>
</div>

<!-- Pin to top left corner -->
<div class="relative h-24 w-24 bg-gray-400">
  <div class="absolute left-0 top-0 h-8 w-8 bg-gray-700"></div>
</div>

<!-- Pin to top right corner -->
<div class="relative h-24 w-24 bg-gray-400">
  <div class="absolute top-0 right-0 h-8 w-8 bg-gray-700"></div>
</div>

<!-- Pin to bottom right corner -->
<div class="relative h-24 w-24 bg-gray-400">
  <div class="absolute bottom-0 right-0 h-8 w-8 bg-gray-700"></div>
</div>

<!-- Pin to bottom left corner -->
<div class="relative h-24 w-24 bg-gray-400">
  <div class="absolute bottom-0 left-0 h-8 w-8 bg-gray-700"></div>
</div>
@endslot
@endcomponent

## Responsive

To position an element only at a specific breakpoint, add a `{screen}:` prefix to any existing positioning utility. For example, adding the class `md:absolute` to an element would apply the `absolute` utility at medium screen sizes and above, and adding `lg:inset-y-0` would apply `inset-y-0` at large screens and above.

For more information about Tailwind's responsive design features, check out the [Responsive Design](/docs/responsive-design) documentation.

@component('_partials.responsive-code-sample')
@slot('none')
<div class="relative h-32 bg-gray-400 p-4">
  <div class="relative bg-gray-800 p-4 text-gray-500">Responsive element</div>
</div>
@endslot

@slot('sm')
<div class="relative h-32 bg-gray-400 p-4">
  <div class="absolute bottom-0 left-0 bg-gray-800 p-4 text-gray-500">Responsive element</div>
</div>
@endslot

@slot('md')
<div class="relative h-32 bg-gray-400 p-4">
  <div class="absolute top-0 inset-x-0 bg-gray-800 p-4 text-gray-500">Responsive element</div>
</div>
@endslot

@slot('lg')
<div class="relative h-32 bg-gray-400 p-4">
  <div class="absolute right-0 inset-y-0 bg-gray-800 p-4 text-gray-500">Responsive element</div>
</div>
@endslot

@slot('xl')
<div class="relative h-32 bg-gray-400 p-4">
  <div class="absolute bottom-0 inset-x-0 bg-gray-800 p-4 text-gray-500">Responsive element</div>
</div>
@endslot

@slot('code')
<div class="relative h-32 bg-gray-400 p-4">
  <div class="none:relative sm:absolute sm:bottom-0 sm:left-0 md:top-0 md:inset-x-0 lg:right-0 lg:inset-y-0 xl:bottom-0 xl:inset-x-0"></div>
</div>
@endslot
@endcomponent

## Customizing

```javascript
module.exports = {
  theme: {
    position: {
      '0': 0,
      auto: 'auto',
    },
  }
}
```

```javascript
module.exports = {
  theme: {
    inset: {
      '0': 0,
      auto: 'auto',
    },
  }
}
```

The classes of the inset live in a new inset plugin instead of the position plugin, so their variants are also controlled separately:

```javascript
module.exports = {
  variants: {
    position: ['responsive'],
    inset: ['responsive'],
  }
}
```