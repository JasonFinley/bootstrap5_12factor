<template>
    <div class="bg-image" >
    <nav class="navbar navbar-light bg-light">
      <button id="btn_msg">歌詞</button> <button id="btn_tb">youtube</button> <button id="btn_bg" class="btn-bg-action">背景</button>
    </nav>
    <div class="song-info">
    <h3 class="text-warning">香水 Perfume</h3>
    <h3 class="text-warning">五月天 Mayday fly to 2022 ［ 好好好想見到你 ］</h3>
    <h5 class="text-warning">詞 ：阿信</h5>
    <h5 class="text-warning">曲 ：冠佑 阿信</h5>
    <iframe class="youtube-player" type="text/html" width="400" height="320" src="http://www.youtube.com/embed/h6WhDdeF40Q" frameborder="0"> </iframe>
    <div class="message">
      <div>十字軍從 東方凱旋 獻上最美 的詩篇</div>
      <div>你的魔法 愛情的霸權 為你臣服 為你捍衛</div>
      <div>為了徹底 描寫你的美 壯烈犧牲 一萬朵玫瑰</div>
      <div>再用虔誠 細細的提煉 讓愛情海 吻在你耳背</div>
      <br>
      <div>啦啦啦啦啦 你想要世界 啦啦啦啦啦 就給你世界</div>
      <div>啦啦啦啦啦 讓感性撒野 啦啦啦啦啦 讓理智全滅</div>
      <div>啦啦啦啦啦 你是 亂世最美的香水</div>
      <br>
      <div>對你深深崇拜 深深迷戀 深深的沉醉</div>
      <div>深深愛上一種 香香的狂顛</div>
      <div>對你深深崇拜 深深迷戀 深深的沉醉</div>
      <div>深深愛上一種 奉獻的哲學</div>
      <div>獻上快樂 獻上傷悲 獻上自我 獻上世界</div>
      <br>
      <div>塞納河畔 鬧市炊煙 混雜人間 小愚昧</div>
      <div>你的出現 將氣氛改寫 空氣轉變 聖潔感覺</div>
      <div>青蘋果是 你野蠻的甜 牛奶與蜜 是你的語言</div>
      <div>沉默尤其 是一種迷迭 當你無心 輕輕的拒絕</div>
      <br>
      <div>馬蹄踏平了國界 野心磨破了披肩 動員了麻瓜魔戒尋找拼湊你的香味</div>
      <div>櫻桃和櫻花纏綿 茉莉和沒藥拼貼 香頌和香榭調配也許再加一點眼淚</div>
      <br>
      <div>就算你沒有答應 就算你也不拒絕 就算我從不打算全身而逃全身而退</div>
      <div>就讓我活到脫軌 就讓我愛到脫線 就讓我為愛而生一千世紀無間輪迴</div>
      <br>
      <div>為你獻上快樂傷悲 為你獻上我的世界</div>
      </div>
    </div>
    </div>
</template>

<script>
/* eslint-disable */
//import $ from "jquery"
// eslint-disable-next-line no-unused-vars
//import jQuery from 'jquery';
//window.$ = window.jQuery = jQuery;
//import '../../node_modules/jquery-backstretch/jquery.backstretch.min.js'
//import 'jquery-backstretch'

var $ = require('jquery');
window.jQuery = $;
require('jquery-backstretch');

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
      backgroundFlag : true,
    }
  },
}

$(document).ready(function(){
  $( "#btn_msg" ).click( function(){
      $(".message").fadeToggle( 3000 );
  });

  $( "#btn_tb" ).click( function(){
      $(".youtube-player").fadeToggle( 3000 );
  });

//  $( "#btn_bg" ).click( function(){
      $(".bg-image").backstretch([
        { url: 'https://picsum.photos/1800/1200?grayscale' },
        { url: 'https://picsum.photos/1800/1200' },
        { url: 'https://picsum.photos/1800/1200?random=1' }
    ], { duration: 3000, transition: 'push_left', transitionDuration: 1000, preload: 1 });
//  });
//'push_left|push_right|cover_up|cover_down|fade'
  $( "#btn_bg" ).click( function(){
    if( $("#btn_bg").hasClass( "btn-bg-action" ) ){
      $("#btn_bg").removeClass( "btn-bg-action" );
      $(".bg-image").backstretch( "pause" );
    }else{
      $("#btn_bg").addClass( "btn-bg-action" );
      $(".bg-image").backstretch( "resume" );
    }
  });

});

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "~bootstrap/scss/bootstrap";

div {
    color: rgb(207, 206, 206);
}
.bg-image {
    min-height: 1200px;
    background-color: #6c757d;
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
}

.btn-bg-action{
  background-color:rgb(251, 255, 0);
  transition-duration: 0.4s;
}
.btn-bg-action:hover {
  background-color: #4c5baf; /* Green */
  color: white;
}

.song-info {
    margin: auto;
    min-width: 420px;
    max-width: 50%;
    min-height: 1200px;
    background-color: rgba(#24242c, 0.5);
}

</style>
