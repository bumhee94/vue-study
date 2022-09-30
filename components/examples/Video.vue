<template>
  <div :class="text">
    <h2>{{text}}</h2>
    <h2>YouTube</h2>
    <!-- youtube 자동재생 설정: autoplay + 크롬자동재생 설정 -->
    <iframe width="934" height="1087" src="https://www.youtube.com/embed/APxCc13Bzng?autoplay=1&mute=1" title="레이저 바실리스크 X 하이퍼스피드 분해 조립" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    <h2>VideoJS</h2>
    <!-- videojs vue 용 -->
    <video ref="videoPlayer" autoplay muted preload="auto" class="video-js"></video>
    <!-- videojs static -->
    <video
      id="my-video"
      class="video-js"
      controls
      preload="auto"
      width="854"
      height="480"
      data-setup="{}"
      autoplay
      muted
    >
      <source src="https://d37hrtj0a49g18.cloudfront.net/2021-06/02_3233_46007/MP4/02_3233_46007_480p.mp4" type="video/mp4" />
      <source src="https://d37hrtj0a49g18.cloudfront.net/2021-06/02_3233_46007/MP4/02_3233_46007_480p.mp4" type="video/mp4" />
      <p class="vjs-no-js">
        하이메이드
        <a href="http://www.e-himart.co.kr/app/display/himadeGoodsShop" target="_blank">하이메이드관 레고레고</a>
      </p>
    </video>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue'
import videojs from 'video.js';
import 'video.js/dist/video-js.min.css';

/**
 * TODO: 영상 자동 실행 기능
 */
export default {
  name: 'Videojs',
  setup() {
    const text = 'Videojs';
    // const videoPlayer = ref();
    const player = ref();
    const options = {
      // 자동실행 여부 => 동작 안함
      // autoplay: true,
      // preload: 'auto',
      // 컨트롤
      controls: true,
      // 동영상 정보
      sources: [
        {
          src: 'https://d37hrtj0a49g18.cloudfront.net/2021-06/02_3233_46007/MP4/02_3233_46007_480p.mp4',
          type: 'video/mp4'
        }
      ]
    }
    let timer = null;

    onMounted(() => {
      console.log('vue setup on mounted.');
      // timer = setInterval(() => {
      //   console.log('timer area.');
      //   console.log(player);
      // }, 1000);
    });

    return { text /*, videoPlayer */, player, options }
  },
  mounted() {
    console.log('vue on mounted.');
    this.player = videojs(this.$refs.videoPlayer, this.options, () => {
      console.log('video playing...');
      // autoplay 안됨.
      // this.options.autoplay = true;
      console.log(this);
    })
  }
}
</script>