<template>
  <div class="flex p-8 justify-center h-screen w-screen bg-gray-50">
    <div>
      <h1 class="font-bold text-4xl mb-8">Turflijst</h1>
      <div class="bg-white shadow-2xl max-w-2xl rounded-xl w-[750px] ">
        <div class="divide-x flex p-8 py-6">

          <!-- Positive -->
          <div class="divide-y flex flex-col gap-6 w-1/2 pr-8">
            <div>
              <label for="quantity-input" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Aantal
                goedgekeurd</label>
              <div class="relative flex items-center max-w-[8rem]">
                <button type="button" id="decrement-button" data-input-counter-decrement="quantity-input"
                  @click="handlePositiveMutation(false)"
                  class="bg-gray-100 dark:bg-gray-700 dark:hover:bg-gray-600 dark:border-gray-600 hover:bg-gray-200 border border-gray-300 rounded-s-lg p-3 h-11 focus:ring-gray-100 focus:ring-2 focus:outline-none">
                  <svg class="w-3 h-3 text-gray-900 dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg"
                    fill="none" viewBox="0 0 18 2">
                    <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                      d="M1 1h16" />
                  </svg>
                </button>
                <input type="text" id="quantity-input" data-input-counter data-input-counter-min="1"
                  data-input-counter-max="50" aria-describedby="helper-text-explanation"
                  class="bg-gray-50 h-11 border-y border-gray-300 text-center text-gray-900 text-sm block w-full py-2.5"
                  placeholder="999" required v-model="positiveCount">
                <button type="button" id="increment-button" data-input-counter-increment="quantity-input"
                  @click="handlePositiveMutation"
                  class="bg-gray-100 dark:bg-gray-700 dark:hover:bg-gray-600 dark:border-gray-600 hover:bg-gray-200 border border-gray-300 rounded-e-lg p-3 h-11 focus:ring-gray-100 focus:ring-2 focus:outline-none">
                  <svg class="w-3 h-3 text-gray-900 dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg"
                    fill="none" viewBox="0 0 18 18">
                    <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                      d="M9 1v16M1 9h16" />
                  </svg>
                </button>
              </div>
            </div>
          </div>

          <!-- Negative -->
          <div class="divide-y flex flex-col gap-6 w-1/2 pl-8">
            <div>
              <label for="quantity-input" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Aantal
                afgekeurd</label>
              <div class="relative flex items-center max-w-[8rem]">
                <button type="button" id="decrement-button" data-input-counter-decrement="quantity-input"
                  @click="handleNegativeMutation(false)"
                  class="bg-gray-100 dark:bg-gray-700 dark:hover:bg-gray-600 dark:border-gray-600 hover:bg-gray-200 border border-gray-300 rounded-s-lg p-3 h-11 focus:ring-gray-100 focus:ring-2 focus:outline-none">
                  <svg class="w-3 h-3 text-gray-900 dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg"
                    fill="none" viewBox="0 0 18 2">
                    <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                      d="M1 1h16" />
                  </svg>
                </button>
                <input type="text" id="quantity-input" data-input-counter data-input-counter-min="1"
                  data-input-counter-max="50" aria-describedby="helper-text-explanation"
                  class="bg-gray-50 h-11 border-y border-gray-300 text-center text-gray-900 text-sm block w-full py-2.5"
                  placeholder="999" required v-model="negativeCount">
                <button type="button" id="increment-button" data-input-counter-increment="quantity-input"
                  @click="handleNegativeMutation"
                  class="bg-gray-100 dark:bg-gray-700 dark:hover:bg-gray-600 dark:border-gray-600 hover:bg-gray-200 border border-gray-300 rounded-e-lg p-3 h-11 focus:ring-gray-100 focus:ring-2 focus:outline-none">
                  <svg class="w-3 h-3 text-gray-900 dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg"
                    fill="none" viewBox="0 0 18 18">
                    <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                      d="M9 1v16M1 9h16" />
                  </svg>
                </button>
              </div>
            </div>
          </div>
        </div>
        <div class="bg-gray-100 p-4 text-center mt-4">
          <span>Totaal</span>
          <div class="text-3xl">{{ negativeCount + positiveCount }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>

const positiveCount = ref(0)

const handlePositiveMutation = (add = true) => {
  if (add) {
    positiveCount.value++
    positiveMutations.value.push({
      count: positiveCount.value,
      time: new Intl.DateTimeFormat('nl-NL', {
        hour: 'numeric',
        minute: 'numeric',
      }).format(new Date())
    })
  } else {
    positiveCount.value--
    positiveMutations.value.pop()
  }
}

const positiveMutations = ref([])


// Negative
const negativeCount = ref(0)

const handleNegativeMutation = (add = true) => {
  if (add) {
    negativeCount.value++
    negativeMutations.value.push({
      count: negativeCount.value,
      time: new Intl.DateTimeFormat('nl-NL', {
        hour: 'numeric',
        minute: 'numeric',
      }).format(new Date())
    })
  } else {
    negativeCount.value--
    negativeMutations.value.pop()
  }
}

const negativeMutations = ref([])

</script>
