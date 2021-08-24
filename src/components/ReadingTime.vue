<template>
  <span>
    <span :title="text">{{ emojis }}</span>
    {{ text }}
  </span>
</template>

<script>
const timings = {
  0.5: '🍪',
  3: '☕',
  12: '🫖',
};

export default {
  props: {
    time: {
      type: Number,
      default: 0,
    },
  },

  computed: {
    emojis() {
      let { time } = this;
      let str = '';

      [12, 3, 0.5].forEach((num) => {
        while (time >= num) {
          time -= num;
          str += timings[num];
        }
      });

      return str;
    },
    text() {
      const { time } = this;
      const lastNumeral = time.toString()[time.toString().length - 1];
      let ending = '';
      if (['1'].includes(lastNumeral)) {
        ending = 'а';
      } else if (['2', '3', '4'].indexOf(lastNumeral)) {
        ending = 'и';
      }

      return `${time} хвилин${ending} чтива`;
    },
  },
};
</script>

