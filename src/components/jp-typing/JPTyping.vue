<template>
  <p class="jp-typing"><span v-for="c in letters" :key="c">{{ c }}</span></p>
</template>

<script setup lang="ts">
import {defineProps, ref, watchEffect} from "vue";

const props = defineProps({
  // The array of strings we want to displayed
  strings: Array,
  // The speed we want to write every string.
  typedSpeed: Number,
  // The time we want to wait before erase the last string.
  waitTime: Number,
  // If we want to loop the animation.
  isLoop: Boolean
});

/*
  This variable allow to split all words from strings to array of chars.
  It's this variable that will be displayed in the spans of template, letter by letter.
 */
const letters = ref([]);

/*
  Write the currentString passed, erase if not the last word or
  if is a loop animation.

  If isLoop, restart the Typing sequence from the first string

  @string currentString: String to write.
  @array strings: All Strings to write.
  @number typedSpeed: The speed we want to write every string.
  @number waitTime: The time we want to wait before erase the last string.
  @boolean isLoop: is a loop animation ?
 */
function typingSequence(currentString, strings, typedSpeed, waitTime, isLoop) {
  // Start to first letter.
  let letterIndex = 0;
  // The first interval allow to push all letter from currentString into the letters array.
  let typed = setInterval(() => {
    // Write letter by letter every {typedSpeed} ms
    setTimeout(() => {
      letters.value.push(currentString.charAt(letterIndex));
      letterIndex++;
    }, typedSpeed)

    // Stop Writing interval if the string is completly typed.
    if (letterIndex == currentString.length) {
      clearInterval(typed);
      // Set new interval to erase text in {waitTime} ms if it's not the last item
      if (strings[strings.length - 1] !== currentString) {
        // Wait {waitTime} ms before erase last string.
        setTimeout(() => {
          // The second interval allow to erase last string letter by letter.
          typed = setInterval(() => {
            setTimeout(() => {
              letters.value.pop();
              letterIndex--;
            }, typedSpeed)

            // When the last string is completly erase, re-run the typingSequence for the next string.
            if (letterIndex == 0) {
              clearInterval(typed);
              typingSequence(strings[strings.indexOf(currentString) + 1], strings, typedSpeed, waitTime, isLoop);
            }
          }, typedSpeed)
        }, waitTime)
      } else {
        if (isLoop) {
          // Interval to erase last string letter by letter if is the last string but it's loop animation.
          setTimeout(() => {
            typed = setInterval(() => {
              setTimeout(() => {
                letters.value.pop();
                letterIndex--;
              }, typedSpeed)

              // When the last string is completly erase, re-run the typingSequence from start.
              if (letterIndex == 0) {
                clearInterval(typed);
                typingSequence(strings[0], strings, typedSpeed, waitTime, isLoop);
              }
            }, typedSpeed)
          }, waitTime)
        }
      }
    }
  }, typedSpeed)
}

watchEffect(() => {
  const { strings, typedSpeed, waitTime, isLoop } = props;
  typingSequence(strings[0], strings, typedSpeed, waitTime, isLoop);
})

</script>

<style scoped lang="scss">
@keyframes blink {
  0% {
    opacity: 0;
  }
  50% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}

.jp-typing {
  &:after {
    content: '|';
    animation: blink infinite .8s;
  }
}
</style>
