<script setup>
	import { reactive } from "vue"
	import SectionTitles from "../components/SectionTitles.vue"
	import ActionBtn from "../components/ActionBtn.vue"
	import SectionLayout from "../components/SectionLayout.vue"

  import { onMounted, onUnmounted, ref } from "vue";

  let currentSlide = ref(0);
  let intervalId;

  const slides = ref([
    {
      image:
          "https://images.pexels.com/photos/19017576/pexels-photo-19017576/free-photo-of-sunflowers-photograpy.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
      category: "Flowers",
      title: "Sunny Sunflowers",
      description: "Beautiful sunflowers shining under the sun.",
    },
    {
      image:
          "https://images.pexels.com/photos/414171/pexels-photo-414171.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
      category: "Landscape",
      title: "Majestic Mountains",
      description:
          "Breathtaking view of majestic mountains and a clear blue sky.",
    },
    {
      image:
          "https://images.pexels.com/photos/5898403/pexels-photo-5898403.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
      category: "Wildlife",
      title: "Graceful Deer",
      description:
          "A graceful deer in its natural habitat, surrounded by greenery.",
    },
    {
      image:
          "https://images.pexels.com/photos/459038/pexels-photo-459038.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
      category: "Waterfall",
      title: "Enchanting Waterfall",
      description: "An enchanting waterfall flowing through a lush forest.",
    },
    {
      image:
          "https://images.pexels.com/photos/2918152/pexels-photo-2918152.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
      category: "Sunset",
      title: "Serene Sunset",
      description:
          "A serene sunset casting warm colors across the sky and water.",
    },
    {
      image:
          "https://images.pexels.com/photos/462162/pexels-photo-462162.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
      category: "Forest",
      title: "Mystical Forest",
      description:
          "A mystical forest with tall trees and soft sunlight filtering through.",
    },
    {
      image:
          "https://images.pexels.com/photos/228095/pexels-photo-228095.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
      category: "Beach",
      title: "Sandy Beach",
      description: "A sandy beach with gentle waves and a clear blue sky.",
    },
    {
      image:
          "https://images.pexels.com/photos/165537/pexels-photo-165537.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
      category: "Mountains",
      title: "Majestic Peaks",
      description: "Majestic mountain peaks covered in snow under a clear sky.",
    },
    {
      image:
          "https://images.pexels.com/photos/19017576/pexels-photo-19017576/free-photo-of-sunflowers-photograpy.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
      category: "Lake",
      title: "Tranquil Lake",
      description: "A tranquil lake surrounded by lush greenery and mountains.",
    },
    {
      image:
          "https://images.pexels.com/photos/228095/pexels-photo-228095.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
      category: "Countryside",
      title: "Idyllic Countryside",
      description:
          "Idyllic countryside scenery with rolling hills and a clear blue sky.",
    },
  ]);


  const startSlider = () => {
    intervalId = setInterval(() => {
      currentSlide.value++;
      if (currentSlide.value >= slides.value.length) {
        currentSlide.value = 0;
      }
    }, 3000);
  };

  onMounted(() => {
    startSlider();
  });

  onUnmounted(() => {
    clearInterval(intervalId);
  });


	const data = reactive({

		actionsBtn: [
			{
				title: "SEE Featuers",
				url: "#services",
			},
			{
				title: "pricing",
				url: "#price",
			},
		],
	})
</script>
<template>
        <div class="w-full h-auto sliderAx">
          <div
              v-for="(slide, index) in slides"
              :key="index"
              v-show="currentSlide === index"
              class="w-full h-auto mx-auto"
          >
            <div
                :style="{ backgroundImage: 'url(' + slide.image + ')' }"
                class="object-fill h-[600px] px-20 py-24 text-white bg-cover"
            >
              <div class="md:w-1/2">
                <p class="mb-5 text-2xl font-bold text-red-300 uppercase text-stroke">
                  {{ slide.category }}
                </p>
                <p class="mb-5 text-3xl font-bold text-yellow-500 text-stroke">
                  {{ slide.title }}
                </p>
                <p
                    class="mb-10 text-2xl font-bold leading-none text-stroke stroke-red-300"
                >
                  {{ slide.description }}
                </p>
                <div class="space-x-1">
                  <ActionBtn v-for="(item, index) in data['actionsBtn']" :key="index" :href="item['url']" v-bind="item" class="font-semibold uppercase px-7 py-3 rounded-full text-xs text-blue-600 border border-blue-600 g-blue-600 hover:text-white hover:bg-blue-600">{{ item["title"] }}</ActionBtn>
                </div>
              </div>
            </div>
          </div>
        </div>

</template>
