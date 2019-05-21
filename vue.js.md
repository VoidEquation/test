##Dynamic components with dynamic imports

```javascript
<template>
	<div class="card">
		<component v-bind:is="componentFile"></component>
	</div>
</template>
<script>
export default{
	props: {
		componentName: {
			type: String,
			required: true
		}
	}
	computed: {
		componentFile() {
			return () => import(`./widgets/${this.componentName}.vue`);
		}
	}
}
</script>
```
