<template>
  <div>
    <FormulateForm v-model="values" :schema="schema" />
    {{ values }}
  </div>
</template>

<script>
export default {
  name: "FormFieldsGen",

  data() {
    return {
      formCopySchema: [],
      values: {},
      isLoading: false,
      schema: [
        {
          type: "group",
          repeatable: true,
          name: "addresses",
          addLabel: "+ Address",
          children: [
            {
              name: "street",
              label: "Street address"
            },
            {
              name: "city",
              label: "City"
            },
            {
              component: "div",
              class: "double-row",
              children: [
                {
                  name: "state",
                  type: "select",
                  label: "State",
                  options: {
                    va: "Virginia",
                    fl: "Florida",
                    ne: "Nebraska",
                    ca: "California"
                  }
                },
                {
                  name: "zip",
                  label: "Zip"
                }
              ]
            }
          ]
        }
      ]
    };
  },
  mounted() {
    this.formCopySchema = [...this.schema];
  },
  methods: {
    submitHandler(data) {
      console.log(data);
    }
  }
};
</script>
