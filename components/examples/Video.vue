<template>
  <div :class="text">
    <h2>{{text}}</h2>
    <h2>YouTube</h2>
    <!-- <button @click="isShow = !isShow">youtube on/off</button> -->
    <!-- youtube 자동재생 설정: autoplay + 크롬자동재생 설정 -->
    <iframe  src="https://www.youtube.com/embed/APxCc13Bzng?autoplay=1&mute=1" title="레이저 바실리스크 X 하이퍼스피드 분해 조립" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen width="1000" height="500"></iframe>
    <div style="margin-bottom: 100px;"></div>
    <h2>VideoJS</h2>
    <!-- videojs vue 용 -->
    <video id="1" ref="videoPlayer" playsinline muted class="video-js"></video>
    <div style="margin-bottom: 100px;"></div>
    <!-- videojs static -->
    <video
      id="2"
      class="video-js"
      controls
      data-setup="{}"
    >
      <source src="https://d37hrtj0a49g18.cloudfront.net/2021-06/02_3233_46007/MP4/02_3233_46007_480p.mp4" type="video/mp4" />
      <source src="https://d37hrtj0a49g18.cloudfront.net/2021-06/02_3233_46007/MP4/02_3233_46007_480p.mp4" type="video/mp4" />
      <p class="1">
        하이메이드
        <a href="http://www.e-himart.co.kr/app/display/himadeGoodsShop" target="_blank">하이메이드관 레고레고</a>
      </p>
    </video>
  </div>
</template>

<script>
import { ref, onMounted, reactive } from 'vue'
import videojs from 'video.js';
import 'video.js/dist/video-js.min.css';

/**
 * TODO: 영상 자동 실행 기능
 */
export default {
  name: 'Videojs',
  setup() {
    const text = 'Videojs';
    const isShow = ref(false);
    const playList = reactive([]);
    // const player = ref({});
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
    };

    // 화면 제어 => TODO: 스크롤 이벤트가 스크롤 시, 발생하지 않아서 확인 필요(overflow, body에 이벤트 주는 등 시도해보았지만, 제대로 잡히지 않았다)
    const handleScroll = (e) => {
      console.log("scroll########################################");
      // console.log(e);
      // video object 찾기
      const objVideos = document.querySelectorAll('video');
      const youtubes = document.querySelector("iframe").contentWindow;
      console.log(youtubes);
      // console.log(objVideos);
      if (objVideos) {
        //console.log('video for >');
        // for (let video of document.querySelectorAll('video')) {
        for (let i = 0; i < objVideos.length; i++) {
          const video = objVideos[i];
          const addPlayerId = video.playerId;
          // video가 없거나, playerId가 없으면 패스
          if (!(video !== undefined && addPlayerId !== undefined)) {
            continue;
          } else {
            // console.log(`top: ${video.getBoundingClientRect().top}  /bottom: ${video.getBoundingClientRect().bottom}`);
          }
          let isPlayList = false;
          playList.forEach(obj => {
            // 플레이 리스트에 동영상이 있는지 체크
            if (obj.playerId === addPlayerId) {
              isPlayList = true;
              // obj.yTop = video.getBoundingClientRect().top;   // 영상 상단 위치
              // obj.yBot = video.getBoundingClientRect().bottom;// 영상 하단 위치
            }
          });
          // 플레이 리스트에 없으면, 목록 추가
          if (!isPlayList) {
            // console.log(`${video.playerId} 목록에 추가!`);
            // console.log(video);
            playList.push({
              playerId: addPlayerId,
              isPlaying: false,
              yTop: video.getBoundingClientRect().top,
              yBot: video.getBoundingClientRect().bottom
            });
          }
        }
        // console.log('추가된 플레이 리스트');
        // console.log(playList);
        playList.forEach((el,idx,list) => {
          const yTop = el.yTop;
          const yBot = el.yBot;
          // 플레이 영역은 화면 1/10 ~ 9/10 영역에 영상 중앙이 위치해 있을 경우, 플레이 => TODO: 정확한 스크롤 위치가 잡히지 않아서 수정 필요
          const psblTop = /* 스크롤 위치(보여지는 화면 상단 기준) */ window.scrollY + /* 브라우저에 보여지는 상단부터 하단까지의 높이 */ window.innerHeight / 10;
          const psblBot = window.scrollY + window.innerHeight * 9 / 10;
          
          const isPlayY = yBot > 0 && psblTop < yBot && yTop < psblBot;
          //const isPlayY = window.scrollY < psblTop && window.scrollY > yTop;
          if (isPlayY && !el.isPlaying) {
            console.log(`${el.playerId} is played.`);
            el.isPlaying = true;
            videojs(el.playerId).play();
            console.log("yTop:::" + yTop);
            console.log("yBot:::" + yBot);
            console.log("psblTop:::" + psblTop);
            console.log("psblBot:::" + psblBot);
            console.log("scrollY:::" + window.scrollY);
            console.log(`${yBot + ' > 0 && psblTop:' + psblTop + ' < yBot:' + yBot + ' && yTop:' + yTop + ' < psblBot:' + psblBot}`);
          } else if (!isPlayY && el.isPlaying) {
            // 플레이 영역이 아닌 영상이 플레이 중일 때, 일시정지
            console.log(`${el.playerId} is paused.`);
            el.isPlaying = false;
            videojs(el.playerId).pause();
            console.log("yTop:::" + yTop);
            console.log("yBot:::" + yBot);
            console.log("psblTop:::" + psblTop);
            console.log("psblBot:::" + psblBot);
            console.log("scrollY:::" + window.scrollY);
            console.log(`${yBot + ' > 0 && psblTop:' + psblTop + ' < yBot:' + yBot + ' && yTop:' + yTop + ' < psblBot:' + psblBot}`);
          }
        });
      }
    };

    onMounted(() => {
      console.log('mounted called.');
      window.addEventListener('scroll', handleScroll);
    });

    return { text, isShow/*, videoPlayer */, playList/*, player*/, options, handleScroll }
  },
  data: ()=> {
    return {
      player: {},
      dispWidth: 100
    }
  },
  mounted() {
    console.log('vue on mounted.');
    this.dispWidth = window.innerWidth;
    this.player = videojs(this.$refs.videoPlayer, this.options, () => {
      // console.log('video playing...');
      // autoplay 안됨.
      // this.options.autoplay = true;
      // console.log(this);
    });
    // document.addEventListener('scroll', this.handleScroll);

    // this.player.on(['waiting', 'pause'], function(e) {
    //   console.log(`${e} is paused.`)
    //   // isPlaying = false;
    // });
    // this.player.on('playing', function(e) {
    //   console.log(`${e} is playing.`)
    //   // isPlaying = true;
    // });
  }
}
</script>