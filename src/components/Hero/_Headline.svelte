<!-- 
@component
### Headline component 
Renders a h1 tag in the style of the Immersive Template.
Wrap this component around the markup you want rendered.

#### Example
```svelte
<Headline>Lorem ipsum dolor sit amet consectetur adipiscing elit</Headline>
```
-->

<script>
  /** @type {{children?: function;}} */
  let { children } = $props();
</script>

<h1 class="font-[publico-headline-black] text-[4rem] text-text-primary">
  {@render children?.()}
</h1>
