# Production Grade Vue
#programming #js #vue
## html
Вместо использования стандартного синтаксиса для props и events
``` vue
<MyComponent
	:options="options"
	:value="value"
	@input="onInput"
	@change="onChange"
/>
```
можно использовать объектный синтаксис:
``` vue
<MyComponent
	v-bind="{options, value}"
	v-on="{input: onInput, change: onChange}"
/>
// либо
<MyComponent
	v-bind="vmsProps"
	v-on="vmsEvents"
/>
```

## css
Вместо использования scoped в стилях лучше использовать css модули
``` vue
<template>
	<p :class="$style.red">
		This is red text
	</p>
</template>

<style module>
.red {
	color:red;
}
</style>
```
Это позволяет получить уникальные классы для каждого элемента:
``` vue
// MyRedText.vue
<template>
	<p :class="MyRedText_red_3fj4x">
		This is red text
	</p>
</template>

<style module>
.MyRedText_red_3fj4x {
	color:red;
}
</style>
```
В отличии от scoped при этом способе не встречается коллизий классов.
Также в случае использования модулей возможно экспортировать ???
> Нужно узнать подробнее
```
<template>
	<p>Grid Padding: {{ $style.gridPadding }}</p>
</template>

<style module>
:export {
	gridPadding: 1.5rem;
}
</syle>
```
