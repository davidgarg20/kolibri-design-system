<template>

  <table>
    <thead>
      <tr>
        <th>Name</th>
        <th class="stretch">
          Description
        </th>
        <th>Type</th>
        <th>Default</th>
        <th>Required</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(prop, i) in api" :key="i">
        <td class="first-col">
          <code>{{ prop.name }}</code>
          <DocsAnchorTarget :anchor="`#prop:${prop.name}`" />
        </td>
        <td>
          <vue-simple-markdown v-if="prop.description" :source="prop.description" />
          <KEmptyPlaceholder v-else />
        </td>
        <td><code>{{ prop.type.name }}</code></td>
        <td>
          <code v-if="prop.defaultValue">
            {{ prop.defaultValue.value }}
          </code>
          <KEmptyPlaceholder v-else />
        </td>
        <td>
          <KEmptyPlaceholder v-if="!prop.required" />
          <code v-else>true</code>
        </td>
      </tr>
    </tbody>
  </table>

</template>


<script>

  export default {
    name: 'PropsTable',
    props: {
      api: {
        type: Array,
        required: true,
      },
    },
  };

</script>


<style lang="scss" scoped>

  @import './styles';

</style>
