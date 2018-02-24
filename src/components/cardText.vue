<template>
  <div v-html="formattedText()"></div>
</template>

<script>
export default {
  props: ['text'],
  methods: {
    formattedText() {
      let result = this.text;
      var patterns = [
        {
          key: '\↵',
          value: '<br/>'
        },
        {
          key: '\{T\}',
          value: '<i class="ms ms-tap"></i>'
        },
        {
          key: '\{C\}',
          value: '<i class="ms ms-c ms-cost"></i>'
        },
        {
          key: '\{E\}',
          value: '<i class="ms ms-e ms-cost"></i>'
        },
        {
          key: '\{R\}',
          value: '<i class="ms ms-r ms-cost"></i>'
        },
        {
          key: '\{U\}',
          value: '<i class="ms ms-u ms-cost"></i>'
        },
        {
          key: '\{W\}',
          value: '<i class="ms ms-w ms-cost"></i>'
        },
        {
          key: '\{B\}',
          value: '<i class="ms ms-b ms-cost"></i>'
        },
        {
          key: '\{G\}',
          value: '<i class="ms ms-g ms-cost"></i>'
        },
        {
          key: '\\{1\\}',
          value: '<i class="ms ms-1 ms-cost"></i>'
        },
        {
          key: '\\{2\\}',
          value: '<i class="ms ms-2 ms-cost"></i>'
        },
        {
          key: '\\{3\\}',
          value: '<i class="ms ms-3 ms-cost"></i>'
        },
        {
          key: '\\{4\\}',
          value: '<i class="ms ms-4 ms-cost"></i>'
        },
        {
          key: '\\{5\\}',
          value: '<i class="ms ms-5 ms-cost"></i>'
        }
      ]

      for (var index in patterns) {
        var pattern = patterns[index];
        result = result.replace(new RegExp(pattern.key, 'g'), pattern.value);
      }
      return result;
    }
  }

}
</script>

