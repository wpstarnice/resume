<template>
  <div class="page projects" :style="{
    background: $store.state.data.website.projects[sections[currentIndex]].background
  }"
  :class="$store.state.data.website.projects[sections[currentIndex]].fontClass ?
  $store.state.data.website.projects[sections[currentIndex]].fontClass : ''">
    <h1 class="title">{{ $store.state.data.route[id] }}</h1>
    <div class="pagebody">
      <section
        class="flexRow allCenter section"
        v-for="(project, index) in sections"
        :class="{
          currentSection: index === currentIndex,
          preSection: index === currentIndex - 1,
          nextSection: index === currentIndex + 1
        }"
        :style="{
          'flex-direction': $store.state.data.website.projects[project].posi === 'left' ? 'row' : 'row-reverse'
        }">
        <div class="flexCol desc">
          <h1 class="descTitle">
            {{ $store.state.data.website.projects[project].title }}
          </h1>
          <h3 class="subTitle">
            {{ $store.state.data.website.projects[project].subTitle }}
          </h3>
          <p class="description">
            {{ $store.state.data.website.projects[project].desc }}
          </p>
          <a class="flexRow allCenter link" target="_blank"
            v-if="$store.state.data.website.projects[project].link"
            :href="$store.state.data.website.projects[project].link">
            <svg viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="24" height="24">
                <path d="M630.88 528.36c-7.264 0-14.512-0.576-21.664-1.736l73.896-73.936 0.568-0.376a27.52 27.52 0 0 0 3.336-2.872l100.792-101.056c30.944-31.016 30.944-81.488 0-112.504a78.68 78.68 0 0 0-56.112-23.304 78.848 78.848 0 0 0-56.152 23.304l-96.68 96.96-4.304 4.192-76.824 76.832c-6.424-42.224 7.424-85.632 37.76-116.064l100.92-101.208a133.68 133.68 0 0 1 95.264-39.576c35.984 0 69.824 14.056 95.272 39.576 52.552 52.688 52.552 138.408 0 191.08L726.024 488.904a133.48 133.48 0 0 1-95.144 39.456z"></path>
                <path d="M391.624 661.72a28.304 28.304 0 0 1-28.256-28.264c0-7.856 3.224-15.184 9.096-20.656L612.56 372.664c5.648-6.064 12.976-9.288 20.832-9.288a28.28 28.28 0 0 1 28.248 28.256 28.24 28.24 0 0 1-8.16 19.864l-6.112 6.232 0.064 0.048-230.576 230.584-0.056-0.032-5.088 4.936a27.92 27.92 0 0 1-20.088 8.456z"></path>
                <path d="M292.288 867a133.672 133.672 0 0 1-95.264-39.56c-52.536-52.688-52.536-138.44 0-191.128l100.92-101.184a133.456 133.456 0 0 1 95.104-39.456c7.128 0 14.224 0.56 21.248 1.68l-76.152 76.136a10.84 10.84 0 0 0-0.672 0.528L236.152 675.64c-30.928 31.016-30.928 81.472 0 112.472a78.792 78.792 0 0 0 56.136 23.312 78.696 78.696 0 0 0 56.112-23.312l100.92-101.168c0.656-0.656 1.24-1.392 1.8-2.128l75.056-75.144c6.608 42.392-7.216 86-37.688 116.592l-100.96 101.176a133.6 133.6 0 0 1-95.24 39.56z"></path>
              </svg>
            <span>{{ $store.state.data.website.projects[project].linkRefer }}</span>
          </a>
        </div>
        <img class="mockup" :src="$store.state.data.website.projects[project].mainImage">
      </section>
      <div class="prePageBtn" @click="prePage" @touchstart="prePage">
        <svg viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="50" height="50">
          <path d="M480 64C214.912 64 0 278.912 0 544 0 809.088 214.912 1024 480 1024c265.088 0 480-214.912 480-480C960 278.912 745.088 64 480 64zM480 960C250.624 960 64 773.376 64 544S250.624 128 480 128 896 314.624 896 544 709.376 960 480 960z"></path>
          <path d="M542.528 767.616c-8.192 0-16.384-3.136-22.656-9.344L328.32 566.656c-0.064 0-0.064-0.064-0.064-0.064 0 0 0 0-0.064-0.064 0 0 0 0 0 0 0 0 0 0-0.064-0.064l0 0c0 0 0 0-0.064-0.064l0 0c0 0-0.064-0.064-0.064-0.064s0 0 0 0c0 0 0.448 0 0.448-0.064l0 0C322.624 560.256 320 552.512 320 544.768l0 0c0 0 0-0.064 0-0.064 0 0-0.512 0-0.512 0 0 0-0.256 0-0.256-0.064 0 0 0.384 0 0.384 0 0 0 0.384 0 0.384-0.064 0 0 0 0 0-0.064l-0.512 0c0 0-0.256 0-0.256-0.064 0 0-0.128 0-0.128 0 0 0-0.064 0-0.064-0.064 0 0 0 0 0 0 0 0 0 0 0-0.064l0 0 0 0c0 0 0-0.064 0-0.064 0 0 0 0 0 0 0 0 0-0.064 0-0.064 0 0 0 0 0 0 0 0 0.512-0.064 0.512-0.064l0.512 0c0-0.064 0-0.064 0-0.064 0 0-0.512-0.064-0.512-0.064 0 0-0.256 0-0.256 0 0 0 0.384-0.064 0.384-0.064 0 0 0.384 0 0.384 0 0 0 0-0.064 0-0.064l0 0c0-7.808 2.624-15.488 8.448-21.504l0 0c0 0-0.192-0.064-0.192-0.064 0 0-0.064 0-0.064 0s0 0 0-0.064l0 0c0 0 0 0 0-0.064l0 0c0 0 0.064-0.064 0.064-0.064 0 0 0 0 0 0 0 0 0 0 0.064-0.064 0 0 0 0 0.064-0.064l192.768-192.832c12.48-12.48 32.768-12.48 45.248 0s12.48 32.768 0 45.248L396.224 544.064l168.896 168.96c12.48 12.48 12.48 32.768 0 45.248C558.848 764.48 550.656 767.616 542.528 767.616z"></path>
        </svg>
      </div>
      <div class="nextPageBtn" @click="nextPage" @touchstart="nextPage">
        <svg viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="50" height="50">
          <path d="M544 960c265.089 0 480-214.912 480-480s-214.912-480-480-480c-265.089 0-480 214.912-480 480 0 265.089 214.912 480 480 480zM544 64c229.376 0 416 186.625 416 416s-186.625 416-416 416-416-186.625-416-416 186.625-416 416-416z"></path>
          <path d="M481.472 256.384c8.193 0 16.384 3.136 22.656 9.344l191.552 191.616c0.064 0 0.064 0.064 0.064 0.064s0 0 0.064 0.064c0 0 0 0 0 0 0 0 0 0 0.064 0.064v0c0 0 0 0 0.064 0.064v0c0 0 0.064 0.064 0.064 0.064s0 0 0 0-0.448 0-0.448 0.064v0c5.824 6.016 8.448 13.76 8.448 21.504v0c0 0 0 0.064 0 0.064s0.512 0 0.512 0c0 0 0.256 0 0.256 0.064 0 0-0.385 0-0.385 0 0 0-0.385 0-0.384 0.064 0 0 0 0 0 0.064h0.512c0 0 0.256 0 0.256 0.064 0 0 0.129 0 0.129 0 0 0 0.064 0 0.064 0.064 0 0 0 0 0 0 0 0 0 0 0 0.064v0 0c0 0 0 0.064 0 0.064s0 0 0 0 0 0.064 0 0.064c0 0 0 0 0 0 0 0-0.512 0.064-0.512 0.064h-0.512c0 0.064 0 0.064 0 0.064s0.512 0.064 0.512 0.064c0 0 0.256 0 0.256 0 0 0-0.384 0.064-0.384 0.064 0 0-0.385 0-0.385 0 0 0 0 0.064 0 0.064v0c0 7.808-2.624 15.488-8.448 21.504v0c0 0 0.192 0.064 0.192 0.064s0.064 0 0.064 0 0 0 0 0.064v0c0 0 0 0 0 0.064v0c0 0-0.064 0.064-0.064 0.064s0 0 0 0 0 0-0.064 0.064c0 0 0 0-0.064 0.064l-192.768 192.832c-12.48 12.48-32.768 12.48-45.248 0s-12.48-32.768 0-45.248l170.239-169.664-168.896-168.96c-12.48-12.48-12.48-32.768 0-45.248 6.272-6.208 14.464-9.344 22.592-9.344z"></path>
        </svg>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'projects',
  props: ['id', 'show'],
  data: () => ({
    sections: [],
    currentIndex: 0
  }),
  beforeMount () {
    this.sections = Object.keys(this.$store.state.data.website.projects)
  },
  mounted () {
    window.addEventListener('keydown', this.keyDown)
  },
  methods: {
    prePage () {
      this.currentIndex = this.currentIndex === 0 ? this.sections.length - 1 : this.currentIndex - 1
    },
    nextPage () {
      this.currentIndex = this.currentIndex === this.sections.length - 1 ? 0 : this.currentIndex + 1
    },
    keyDown (event) {
      if (this.show) {
        if (event.keyCode === 37) { // left
          this.prePage()
        } else if (event.keyCode === 39) {  // right
          this.nextPage()
        }
      }
    }
  }
}
</script>

<style lang="less" scoped>
@import 'index.less';
</style>
