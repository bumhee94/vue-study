<template>
  <div :class="text">
    <h2>{{text}}</h2>
    <div v-html="vHtml"></div>
  </div>
</template>

<script>
import { onMounted } from 'vue';

/**
 * html script 포함 컨텐츠 동작 테스트
 * - script 태그 닫을 때 이스케이프 처리만 잘해주면 된다.
 */
export default {
  name: 'Html',
  setup() {
    const text = 'Html';

	onMounted(() => {
		let scripts = [
			"https://cdn.jsdelivr.net/npm/swiper@8/swiper-bundle.min.js",
			"https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"
		];
		scripts.forEach(script => {
			let tag = document.createElement("script");
			tag.setAttribute("src", script);
			document.head.appendChild(tag);
		});

		// TODO: 컨텐츠 등록만으로 swiper가 동작해야 한다.
		// let tutorial = new Swiper('.tutorial .swiper-container', {
        //     slidesPerView: 'auto',
        //     loop: true,
        //     pagination: {
        //         el: '.swiper-pagination',
        //     },
        // });
	});

    const vHtml = `<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@8/swiper-bundle.min.css" />
	<style type="text/css">/* 공통 */
    .event10697 {position: relative; overflow: hidden;}
    .event10697 .section {position: relative; display: block;}
    .event10697 .btn {position: absolute; top: 0; left: 50%; transform: translateX(-50%); width: 86.668%;}
    .event10697 .evt_banner {display: block;}

    /* 버튼 */
    .event10697 .btn {position: absolute; top: 0; left: 50%; transform: translateX(-50%); width: 86.668%;}
    .event10697 .btn.floating {display: block; top: 72.897%; padding: 4.6% 0; background: #343167; background-size: 100%; border-radius: 1.333333vw; z-index: 99; transition: width .3s;}
    .event10697 .btn.floating img {width: 37.694%; margin: 0 auto;}
    .event10697 .btn.floating.complete {padding: 4.6% 0; background: #626262; background-size:100%;}
    .event10697 .btn.floating.complete img {width: 38.31%;}
    .event10697 .btn.floating.on {position: fixed; top: 72.40%; width: 100%;}
    .event10697 .btn.floating.active {border-radius: 0;}
    .event10697 .btn.btn_app {top: 72.897%; width: 86.134%; padding: 4.934% 0; background: transparent; border: 2px solid #525fff; border-radius: 1.333333vw;}
    .event10697 .btn.btn_app img {width: 57.895%; margin: 0 auto;}
    @media screen and (min-width: 750px) {
        .event10697 .btn.floating {border-radius: 10px;}
    }

    /* 튜토리얼 */
    .event10697 .tutorial {background: #8998ff;}
    .event10697 .tutorial .l_inner {position: relative; margin: 0 auto; padding: 0 2.668% 9.335%;}
    .event10697 .tutorial .swiper-wrapper {position: relative; padding: 0;}
    .event10697 .tutorial .swiper-slide {background: none;}
    .event10697 .tutorial .swiper-slide {background: transparent; border-radius: 0.666667vw; overflow: hidden;}
    .event10697 .tutorial .swiper-pagination {display: block; position: static; padding: 4% 0 0;}
    .event10697 .tutorial .swiper-pagination.swiper-pagination-bullets {bottom: 0;}
    .event10697 .tutorial .swiper-pagination .swiper-pagination-bullet {width: 2vw; height: 2vw; margin: 0 0.986%; background: #fdfdfb; opacity: 1;}
    .event10697 .tutorial .swiper-pagination .swiper-pagination-bullet-active {background: #525efe; opacity: 1;}

    /* 이벤트 팝업 커스텀 */
    .hm-app__layer-popup:not(.hm-app__layer-popup--dimm):not(.hm-app__layer-popup--tooltip) .hm-layer-popup__header {text-align: center;}
    .hm-app__layer-popup:not(.hm-app__layer-popup--dimm):not(.hm-app__layer-popup--tooltip) .hm-layer-popup__heading {padding-left: 0;}
    .layerpopup-apply .pop_cont .hm-heading--extra-thick {margin-bottom: 10px;}
    .layerpopup-apply .pop_cont .hm-heading--extra-thick:first-child {margin-top: 0;}
    .layerpopup-apply .pop_cont .hm-heading--extra-thick span {color: #ed4046;}
    .layerpopup-apply .pop_cont .cont_box {margin-top: 30px;}
    .layerpopup-apply .pop_cont .cont_box:first-child {margin-top: 0;}
    .layerpopup-apply .pop_cont .cont_box .hm-box {font-size: 13px;}
    .layerpopup-apply .pop_cont .cont_box .hm-box .information dd {margin-bottom: 20px;}
    .layerpopup-apply .pop_cont .cont_box .hm-box .information strong {color: #000;}
    .layerpopup-apply .pop_cont .cont_box .select_agree {margin: 10px; text-align: right;}
    .layerpopup-apply .pop_cont .cont_box .select_agree label {margin-left: 15px;}
    .layerpopup-apply .pop_cont .cont_box .select_agree label:first-child {margin-left: 0;}
    .layerpopup-apply .hm-btns {margin: 25px 0;}
    .layerpopup-apply .notice {margin-top: 30px; text-align: center;}
</style>
<script>
    $(function () {
        var btnFloating;

        $(window).scroll(function () {
            if (!$(".btn.floating").hasClass('active')) {
                btnFloating = Math.round($(".btn.floating").offset().top) - $(".hm-top-nav").outerHeight();
            }
            if ($(window).scrollTop() > btnFloating) {
                $(".btn.floating").addClass('on');
                $('.btn.floating').css({ top: $('.hm-top-nav').outerHeight()});
                setTimeout(function () {
                    $(".btn.floating").addClass('active');
                }, 1);
            } else {
                $(".btn.floating").removeClass('active');
                setTimeout(function () {
                    $(".btn.floating").removeClass('on');
                    $('.btn.floating').css({ top: '' });
                }, 1);
            }
        });
    }); 
<\/script><script>
    function goBrowser(url) {
        var userAgent = navigator.userAgent.toLowerCase();
        var mobileApp = (/himartapp_android|himartapp_ios/i.test(userAgent));
        if (mobileApp) {
            location.href = "hmapp://gotowebbrowser?" + url;
        } else {
            window.open(url, '_blank');
        }
    }
<\/script>
<div class="event10697"><!-- 상단 -->
<div class="section"><img alt="도전! 베스트 후기! 이사/웨딩 세트 포토후기 작성하고 선물받자!" src="http://static1.e-himart.co.kr/contents/content/upload/event/10697/MC/visual.jpg" /> <!-- 등록하기 --> <a class="btn floating" href="javascript:void(0);" onclick="checkEvtEntry();"> <img alt="후기 등록하기" src="http://static1.e-himart.co.kr/contents/content/upload/event/10697/MC/btn_apply.png" /> </a> <!-- // 등록하기 --> <!-- 등록완료 --> <!-- <span class="btn floating complete">
		<img src="http://static1.e-himart.co.kr/contents/content/upload/event/10697/MC/btn_complete.png" alt="후기 등록완료">
	</span> --> <!-- // 등록완료 --> <!-- APP에서만 --> <!-- <span class="btn btn_app">
		<img src="http://static1.e-himart.co.kr/contents/content/upload/event/10697/MC/btn_app.png" alt="APP에서만 참여 가능합니다.">
	</span> --> <!-- // APP에서만 --></div>
<!-- // 상단 --><!-- 참여 경품 -->

<div class="section"><img alt="후기등록 이벤트 경품 안내" src="http://static1.e-himart.co.kr/contents/content/upload/event/10697/MC/giveaway.jpg" /></div>
<!-- // 참여 경품 --><!-- 참여방법 --><script src="http://mstatic1.e-himart.co.kr/resources/native/js/swiper-event.js"><\/script>

<div class="section tutorial"><img alt="이벤트 참여방법" src="http://static1.e-himart.co.kr/contents/content/upload/event/10697/MC/tit_tutorial.png" />
<div class="l_inner">
<div class="swiper-container">
<div class="swiper-wrapper">
<div class="swiper-slide"><img alt="STEP 1, 하이마트에서 300만원 이상 이사/웨딩 가전/가구 구매하기" src="http://static1.e-himart.co.kr/contents/content/upload/event/10697/MC/tutorial01.png" /></div>

<div class="swiper-slide"><a href="javascript:goBrowser('http://m.blog.naver.com/wjd6/222620464637');"><img alt="STEP 2, 이벤트 페이지를 캡처하고 본인 네이버 블로그에 자신이 캡처한 사진과 함께 구매/사용후기, 혜택 지급후기 등을 정성껏 남기기" src="http://static1.e-himart.co.kr/contents/content/upload/event/10697/MC/tutorial02.png" /> </a></div>

<div class="swiper-slide"><img alt="STEP 3, 현재 이벤트 페이지에 후기 등록하기 버튼을 클릭해 작성한 네이버 블로그 체험후기 링크를 등록하여 이벤트 참여 완료!" src="http://static1.e-himart.co.kr/contents/content/upload/event/10697/MC/tutorial03.png" /></div>
</div>

<div class="swiper-pagination">&nbsp;</div>
</div>
</div>
</div>
<script>
        var tutorial = new Swiper('.tutorial .swiper-container', {
            slidesPerView: 'auto',
            loop: true,
            pagination: {
                el: '.swiper-pagination',
            },
        });
    <\/script><!-- // 참여방법 --><!-- 배너 -->

<div class="evt_banner"><a href="http://m.e-himart.co.kr/app/displayPlan/listPlanDetail?spdpNo=8829"><img alt="하이마트와 함께하는 새출발, 이사/웨딩/다품목 세트구매 자세히 보기" src="http://static1.e-himart.co.kr/contents/content/upload/event/10697/MC/banner01.jpg" /> </a></div>
<!-- // 배너 --><!-- 유의사항 -->

<div class="section"><img alt="꼭 확인해주세요!" src="http://static1.e-himart.co.kr/contents/content/upload/event/10697/MC/notice.jpg" /></div>
<!-- // 유의사항 --></div>
<!-- 레이어 팝업: 응모하기 팝업(등록하기) -->

<div class="hm-app__layer-popup layerpopup-apply" id="layerpopup-apply">
<div class="hm-layer-popup">
<div class="hm-layer-popup__header">
<h1 class="hm-heading hm-layer-popup__heading">이사/웨딩 후기 등록하기</h1>
<button class="hm-layer-popup__close" onclick="closePopup();" type="button">닫기</button></div>

<div class="swiper-container hm-layer-popup__scroll js-layer-contents-slide">
<div class="swiper-wrapper">
<div class="swiper-slide">
<div class="pop_cont">
<div class="cont_box">
<h3 class="hm-heading hm-heading--3 hm-heading--extra-thick">네이버 블로그 공유 URL</h3>
<input class="hm-input" id="applyUrl" type="text" /></div>

<div class="cont_box">
<h3 class="hm-heading hm-heading--3 hm-heading--extra-thick">개인정보 수집&middot;이용 동의</h3>

<div class="hm-box hm-box--sm">
<div class="hm-box__content hm-text-color-md-gray agree">『개인정보보호법』 제 15조 법규에 의거하여 롯데하이마트 주식회사는 고객님의 개인정보 수집 및 이용에 대해 개인정보 수집 및 이용 동의를 받고 있습니다.<br />
<br />
개인정보 제공자가 동의한 내용 외의 다른 목적으로 활용하지 않으며, 제공된 개인정보의 이용을 거부하고자 할 때에는 개인정보 관리책임자를 통해 열람, 정정 혹은 삭제를 요구할 수 있습니다.<br />
<br />
제공된 개인정보는 아래 항목에 한해 제한된 범위에서만 활용됩니다.<br />
&nbsp;
<dl class="information">
	<dt><strong>[개인정보의 수집 및 이용 목적]</strong></dt>
	<dd>- <strong>이벤트 대상자 여부 확인 및 행사&middot;상품 안내</strong></dd>
	<dt><strong>[수집하는 개인정보의 항목]</strong></dt>
	<dd>- <strong>로그인 ID, 휴대전화번호, 이사/웨딩 구매/사용 후기</strong></dd>
	<dt><strong>[개인정보의 보유 및 이용기간]</strong></dt>
	<dd class="information_type">- <strong>행사 시작일로부터 3개월 후</strong> 해당 개인정보를 즉시 파기합니다. (별도 안내 없이 파쇄) 단, 별도의 동의를 받은 경우 또는 관련 법령에 의해 보존할 필요성이 있는 경우에는 법령에서 정한 기간까지 보유할 수 있습니다.</dd>
</dl>
※ 귀하는 개인정보의 수집&middot;이용에 대한 동의를 거부할 권리가 있으며, 동의를 거부하시는 경우 혜택 정보는 제공되지 않습니다.</div>
</div>

<div class="select_agree"><label class="hm-radio"><input class="hm-radio__radio" id="agree1" name="agreetype1" type="radio" value="" /> <span class="hm-radio__label">동의함</span> </label> <label class="hm-radio"> <input class="hm-radio__radio" id="agree2" name="agreetype1" type="radio" value="" /> <span class="hm-radio__label">동의하지 않음</span> </label></div>
</div>

<div class="cont_box">
<h3 class="hm-heading hm-heading--3 hm-heading--extra-thick">개인정보 취급&middot;위탁 동의</h3>

<div class="hm-box hm-box--sm">
<div class="hm-box__content hm-text-color-md-gray agree">이벤트 당첨 및 처리를 위해 일부 개인정보를 제한적으로 제3자에게 제공하여 운영한다.<br />
&nbsp;
<dl class="information">
	<dt><strong>[개인정보를 제공받는 자]</strong></dt>
	<dd>- <strong>대홍기획</strong></dd>
	<dt><strong>[개인정보를 제공받는 자의 이용목적]</strong></dt>
	<dd>- <strong>경품 지급</strong></dd>
	<dt><strong>[제공하는 개인정보 항목]</strong></dt>
	<dd>- <strong>로그인 ID, 핸드폰번호</strong></dd>
	<dt><strong>[개인정보를 제공받는 자의 개인정보 보유 및 이용기간]</strong></dt>
	<dd class="information_type">- <strong>이벤트 종료 후 3개월</strong></dd>
</dl>
개인정보 제3자 재공에 동의하지 않을 권리가 있으며, 동의를 하지 않을 경우에는 본 이벤트 참여가 불가능합니다.</div>
</div>

<div class="select_agree"><label class="hm-radio"><input class="hm-radio__radio" id="agree3" name="agreetype2" type="radio" value="" /> <span class="hm-radio__label">동의함</span> </label> <label class="hm-radio"> <input class="hm-radio__radio" id="agree4" name="agreetype2" type="radio" value="" /> <span class="hm-radio__label">동의하지 않음</span> </label></div>
</div>

<div class="hm-btns"><a class="hm-btn hm-btn--lg hm-btn--red" href="javascript:applyEvent();">확인</a></div>
</div>
</div>
</div>
</div>
</div>
</div>
<!-- // 레이어 팝업: 응모하기 팝업(등록하기) --><script>
	$(document).ready(function(){
		$('#layerpopup-apply').insertAfter('.proBanner');

		if(evtSbscInfoList != '[]' && evtSbscInfoList != '' && evtSbscInfoList != null){
			$(".btn.floating").addClass('complete');
			$('.event10697 .section .btn img').attr('src', 'http://static1.e-himart.co.kr/contents/content/upload/event/10697/MC/btn_complete.png');
			$('.event10697 .section .btn').attr('onclick', 'alert("이미 신청하셨습니다.");');
		}
	});

	// 후기 등록하기 버튼 클릭
	function checkEvtEntry() {
		// if(isLogin == 'false'){
		// 	eventSbscHistory(0, 0, '04');
		// 	if (confirm('하이마트-L.POINT 통합회원 로그인 후 참여하실 수 있습니다.\\n로그인 하시겠습니까?')) {
		// 		location.href = _httpsDomain+'/app/login/login?returnUrl='+_httpDomain+'/app/event/eventDetails?evtNo='+$('#evtNo').val();
		// 	}
		// 	return;
		// }

		// if(evtMbrTpCd != '01'){
		// 	// eventSbscHistory(0, 0, '05');
		// 	alert('하이마트 LPOINT 회원만 참여 가능합니다.');
		// 	return;
		// }

		// if (evtPayAmt < 3000000) {
		// 	// eventSbscHistory('0', '0', '14');
		// 	alert('이벤트 기간 내 하이마트에서 300만원 이상 결제완료한 고객에 한해 응모 가능합니다.');
		// 	return;
		// }

		// 신청하기 팝업 오픈
		// HM.UI.layerPopupShow({layerpopup_selector: '#layerpopup-apply'});
		console.log('checkEvtEntry');
	}

	// 확인 버튼 클릭
	function applyEvent(){
		if($('#applyUrl').val() == '' || $('#applyUrl').val() == null){
			alert('네이버 블로그 공유 URL을 입력 해주세요.');
			$('#applyUrl').focus();
			return;
		}

		var urlVal = $("#applyUrl").val();
		if(!ValidUrl(urlVal)){
			//return "URL형식이 맞지 않습니다.";
			alert('URL형식이 맞지 않습니다.');
			$('#applyUrl').focus();
			return;
		}
		if(urlVal.length>200){
			//$("#applyUrl").val(urlVal.substr(0,200));
			//$("#applyUrl").focus();
			//return "URL길이는 200자까지 입니다."
			alert('URL길이는 200자까지 입니다.');
			$('#applyUrl').focus();
			return;
		}

		if($('#agree1').prop('checked') == false){
			alert('개인정보 수집·이용 동의를 확인해 주십시오.');
			$('#agree1').focus();
			return;


		} else {
			$('#evtFrm #prsnInfoClctnUtilAgrYn').val($('#agree1').val());
		}

		if($('#agree3').prop('checked') == false){
			alert('개인정보 취급·위탁 동의를 확인해 주십시오.');
			$('#agree3').focus();
			return;
		} else {
			$('#evtFrm #prsnInfoSupCnsgAgrYn').val($('#agree3').val());
		}

		$('#evtFrm #sbscCont').val($("#applyUrl").val());
		
		openEventEntry();
	}

	function ValidUrl(str) {
		var pattern = new RegExp('^(https?:\\/\\/)?'+
		'((([a-z\d](([a-z\d-]*[a-z\d])|([ㄱ-힣]))*)\.)+[a-z]{2,}|'+
		'((\\d{1,3}\\.){3}\\d{1,3}))'+ 
		'(\\:\\d+)?(\\/[-a-z\\d%_.~+]*)*'+ 
		'(\\?[;&a-z\\d%_.~+=-]*)?'+ 
		'(\\#[-a-z\\d_]*)?$','i');
		
		if(!pattern.test(str)) {
		  return false;
		} else {
		  return true;
		}
	}

	function closePopup() {
		alert('팝업을 닫으시면 청첩장이 등록되지 않습니다.');		
		HM.UI.layerPopupHide({layerpopup_selector: '#layerpopup-apply'});
	}
<\/script>`;

    return { text, vHtml }
  }
}
</script>