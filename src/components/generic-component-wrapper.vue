<!-- 
This componentn shows a generic approach how to render a dynamic component tree 
with usage of a function component and the component-component.
Example of the object describing the component tree:

{
    id: 1,
    component: "SomeRegisteredComponent",
    options: {},
    children: [
        {
            id: 2,
            component: "AnotherComponent",
            options: {
                text: "My Dynamic Form"
            }
        },
        {
            id: 3,
            component: "MyInputComponent",
            options: {
                type: "text",
                binding: "lastname",
                label: "Last name"
            }
        }
    ]
}

-->

<template functional>
  <component :is="data.attrs.component" v-bind="data.attrs.options">
    <template v-if="data.attrs.children" v-for="child in data.attrs.children">
      <generic-component-wrapper
        :key="child.id"
        v-bind="child"
      ></generic-component-wrapper>
    </template>
    {{ data.attrs.content }}
  </component>
</template>

<script>
export default {
  name: "generic-component-wrapper",
  created() {}
};
</script>
