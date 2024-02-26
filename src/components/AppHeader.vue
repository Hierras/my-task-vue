

<template>
    <header>
        <h1>Список дел</h1>
        <p>
            Всего: {{ allCount }}
            Осталось: {{ lastCount }}
        </p>
        
    </header>

</template>
  
  <script>
  export default {
    props: {
        allCount: {
            type: Number,
            required: true
        },
        lastCount: {
            type: Number,
            required: true
        },
    }
  }
  </script>
  
  <style scoped>
    header {
        text-align: center;
    }
    span {
        color: red;
    }
  </style>