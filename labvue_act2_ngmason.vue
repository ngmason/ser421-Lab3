//https://play.vuejs.org/?trk=public_post-text#__PROD__eNp9VW1v2zYQ/itXAYO7xbGTuNsATR7WBf2wDWi3Nl+GqB9o6WSxoUiVL3ZcQ/+9R1KyZKQNYEPk3XMPn3sRdUxet+1i5zBJk8wUmrf291ziY6u0hRIr5oSFYy4BSmbZyx/jGkCjdVoOO4DPUqVwNT9tHRrLlTQp3M9+gZ/gV1jP5jC7WcEFXF/FzV2NwKTZowarAHeoD7bmcgvcwOzjyBUxgerVzWw+W618NC1HTFErXmCAXBHi2v8JFaDnSGdQ3wZ0CtIJcXKYQmmyjTlUXHJTY5lCxYTBaO78oyOMfzZoa1XSqX0ZjNs03L4OcsdSAfAKXlJmZjEeDuv1GoJtSO8+7qT6OImEiAnaLi5+G8yk4gk3RULWUw7VXwiUW1vDJVw/JaWACWVvnCoM9RnPBKQqPGEZqkRwqx1OJU6U0oN+2fI0YbSx2LSCWaQdQFbyXVjEJewuebXOkxcDfZ70XvK3UAhmDLlrZCVq8v2vnIZbpzVKCx9iJ4/H2FPoOlDOgqpglS3bZ3n+6yvng31BaVi7zlOdSnrvO9R1Z0Re8EDVT+JELwEE26CgnCqlPQS4HCY2TyB9wIO3noVQEJctqbaHFsmrWcmVB++YcN5AcCJsVImCdmPb8mR5RnM8FpR/ttFTc7YMisYMlmP5aTcFZxtnLRXkj0Lw4oGOmg45SX73T7aMkKF9PddZM8PoDCWinjIxyZaaBzXbEUDRRKClYbJ0NXx2/MsLKkNsbmzlnpnv9JV/4/hhnS0ns0ZbYw/CLxex73GmKyXt5R75trYpbJQowygHq+FfaJ6ub65+IFuY6EXfvkloxRouDinkyS3p5UT7Fvd5ModGSWVaVvh3IwaHAsTQQgmlU9hqRDkeOHLd8YZOISZ4rxomPR+1mldPxP08ERf5+URcyDgFbhl1MeLoZezLkMwTSxWVFd8uPhkl6VMQImnIqCFcoH7XhtnPk9NVlydMCLX/O9j8i99fm/4FwOLhG/ZP5tHb8uRfjZTCjib15LNMb9FG95sPb/GR1icnzbgThH7G+R6NEs5rjLA/nSxJ9gQX1P7V+M8afWHuzJtHi9IMSXmhw8Xu0fQ9vH0m9VHuavFquN6S7iuQ2UyM

<script>
export default {
  data() {
    return {
      qno: 0,
      questions: ['6 * 7 =', '23 + 10 =', 'The answer to everything is '],
      qanswers: ['42','33', '42'],
      choices: ['0','1','13','33','42'],
      userChoice: null,
      score: 0,
      finished: false
    }
  },

  methods: {
    submitAnswer() {
      if (this.userChoice === this.qanswers[this.qno]) {
        this.score++;
      }

      if (this.qno < this.questions.length - 1) {
        this.qno++;
        this.userChoice = null;
      } else {
        this.finished = true;
      }
    }

  }
}
</script>

<template>
  <div>
    <div v-if="!finished">
      <p class="header">Your Current Score: {{ score }} out of 3</p>
      <p class="header">Question {{ qno + 1}}: {{questions[qno]}}</p>
      <div class="choices">
        <label v-for="c in choices" :key="c">
          <input type="radio" :value="c" v-model="userChoice"/>
          {{c}} <br/>
        </label>
      </div>
      <br/>
      <button @click="submitAnswer">OK</button>
    </div>

    <div v-else class="final">
      You have completed the quiz! <i>Your score was {{ score }} out of 3</i>
    </div>

  </div>
</template>

<style>
.header {
  font-weight: bold;
  font-size: 120%;
}

.choices {
  font-family: "Courier New", monospace;
}

.final {
  color: green;
  font-family: "Times New Roman", serif;
  font-size: 150%;
}

.final i {
  font-style: italic;
}
</style>