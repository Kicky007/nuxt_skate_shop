<template>
	<div class="contest-details">
		<div class="header-text">
			<p>Contest details</p>
			<p v-if="closed" class="contest-closed">
				Contest Closed!
			</p>
		</div>
		<div class="horizontal-line"></div>
		<div class="detail-item">
			<p class="item-title">Stats</p>
			<div class="content-time">
				<ul>
					<li style="margin-bottom:8px;">
						<span class="icon_time_text">
							<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
								<path d="M10 18.3334C5.865 18.3334 2.5 14.9692 2.5 10.8334C2.5 6.69754 5.865 3.33337 10 3.33337C14.135 3.33337 17.5 6.69754 17.5 10.8334C17.5 14.9692 14.135 18.3334 10 18.3334ZM10 5.00004C6.78333 5.00004 4.16667 7.61671 4.16667 10.8334C4.16667 14.05 6.78333 16.6667 10 16.6667C13.2167 16.6667 15.8333 14.05 15.8333 10.8334C15.8333 7.61671 13.2167 5.00004 10 5.00004Z" fill="#283441"/>
								<path d="M17.6173 6.74833C18.059 6.2975 18.3332 5.68083 18.3332 5C18.3332 3.61917 17.214 2.5 15.8332 2.5C15.1523 2.5 14.5348 2.77417 14.084 3.21667L17.6173 6.74833Z" fill="#283441"/>
								<path d="M2.38258 6.74833C1.94091 6.2975 1.66675 5.68083 1.66675 5C1.66675 3.61917 2.78591 2.5 4.16675 2.5C4.84758 2.5 5.46508 2.77417 5.91591 3.21667L2.38258 6.74833Z" fill="#283441"/>
								<path d="M11.9107 13.9225L9.41067 11.4225C9.254 11.2658 9.1665 11.0541 9.1665 10.8333V6.66663H10.8332V10.4883L13.089 12.7441L11.9107 13.9225Z" fill="#283441"/>
							</svg>
						</span>
						<p><span class="largeTxt">-5 </span> days left</p>
					</li>
					<li>
						<span class="icon_time_text">
							<svg width="20" height="20" viewBox="0 0 20 20" fill="none">
								<path d="M5.09082 14.9091H14.909V5.09091H5.09082V14.9091ZM6.72718 6.72728H13.2726V13.2727H6.72718V6.72728Z" fill="#283441"></path>
								<path d="M14.9093 1H13.2729V3.45455H14.9093V1Z" fill="#283441"></path>
								<path d="M6.72718 1H5.09082V3.45455H6.72718V1Z" fill="#283441"></path>
								<path d="M14.9093 16.5455H13.2729V19H14.9093V16.5455Z" fill="#283441"></path>
								<path d="M6.72718 16.5455H5.09082V19H6.72718V16.5455Z" fill="#283441"></path>
								<path d="M19 5.09091H16.5454V6.72728H19V5.09091Z" fill="#283441"></path>
								<path d="M19 13.2727H16.5454V14.9091H19V13.2727Z" fill="#283441"></path>
								<path d="M3.45455 5.09091H1V6.72728H3.45455V5.09091Z" fill="#283441"></path>
								<path d="M3.45455 13.2727H1V14.9091H3.45455V13.2727Z" fill="#283441"></path>
							</svg>
						</span>
						<p><span class="largeTxt">1 </span> designs submitted</p>
					</li>
				</ul>
			</div>
		</div>
		<div class="detail-item">
			<p class="item-title">Prize pool</p>
			<div class="prize-pool">
				<ul>
					<li>€ 2500 - Cash</li>
					<li>5x Your winning deck design</li>
					<li>500 Pieces of Awesome</li>
				</ul>
			</div>
		</div>
		<div class="detail-item">
			<p class="item-title">Design files</p>
			<div class="design-files">
				<ul>
					<li>
						<p>Complete briefing (.pdf)</p>
						<btn-text btnClass="btn gray sm" :btnDisabled="closed">Download</btn-text>
					</li>
					<li>
						<p>Templates and Graphics files (.zip)</p>
						<btn-text btnClass="btn gray sm" :btnDisabled="closed">Download</btn-text>
					</li>
				</ul>
			</div>
		</div>
		<btn-text btnClass="btn dark lg" :btnDisabled="closed">Download all files</btn-text>
		<div class="detail-item" style="margin-top: 40px;">
			<p class="item-title">Submission terms</p>
			<p class="item-text">
				Please read our submission Terms and Conditions carefully before submitting your design. It’s very short, easy to read and important!
			</p>
			<p class="item-text mobile-toast" v-if="$device.isMobile">
				Submitting designs on a mobile phone is not possible at this time. Please use a device with a larger screen to upload your design.
			</p>
		</div>
		<nuxt-link :to="`/contests/1/upload`" v-if="!$device.isMobile">
			<btn-text btnClass="btn primary lg" :btnDisabled="closed">Submit your design</btn-text>
		</nuxt-link>
		
	</div>
</template>

<script>
export default {
	props:{
		closed:{
			type: Boolean,
			default: false
		}
	}
}
</script>

<style lang="scss" scoped>
@import "~assets/css/variable.scss";
.contest-details{
	width:100%;
}
.header-text{
	display: flex;
	justify-content: space-between;
	align-items: flex-end;
	margin-bottom: 20px;
}
.header-text p{
	font-family: $font-family-primary;
	font-style: normal;
	font-weight: bold;
	font-size: 24px;
	line-height: 1;
	color: #283441;
}
p.contest-closed{
	font-family: $font-family-primary;
	font-style: normal;
	font-weight: 600;
	font-size: 14px;
	line-height: 1;
	text-align: right;
	color: #F5404C;
}
.horizontal-line{
	width: 100%;
	border: 1px solid #E7E8EA;
	margin-bottom: 20px;
}
.detail-item{
	margin-bottom: 40px;
}
p.item-title{
	font-family: $font-family-primary;
	font-style: normal;
	font-weight: 600;
	font-size: 14px;
	line-height: 19px;
	color: #283441;
	margin-bottom: 10px;
}
.content-time{
	max-width: 391px;
	width: 100%;
	margin-right: 31px;
	display: flex;
	align-items: center;
	justify-content: space-between;
}
.content-time ul li{
	display: flex;
}
.icon_time_text{
	margin-right: 15px;
}
.content-time ul li p{
	font-size: 14px;
	line-height: 180%;
	color: #283441;
	font-family: $font-family-primary;
	font-style: normal;
	font-weight: 300;
}
.largeTxt{
	font-family: $font-family-primary;
	font-style: normal;
	font-weight: bold;
	font-size: 16px;
	line-height: 22px;
	color: #283441;
}
.prize-pool ul{
	list-style: disc;
	list-style-position: inside;
	font-family: $font-family-primary;
	font-style: normal;
	font-weight: bold;
	font-size: 16px;
	line-height: 22px;
	color: #283441;
}
.prize-pool ul li{
	margin-top:10px;
}
.design-files ul{
	list-style: disc;
	list-style-position: inside;
	font-family: $font-family-primary;
	font-style: normal;
	font-weight: normal;
	font-size: 14px;
	line-height: 19px;
	color: #283441;
	letter-spacing: 0.02em;
	margin-bottom: 20px;
}
.design-files ul li{
	margin-top:10px;
	padding-left:20px;
	position: relative;
	display: flex;
	justify-content: space-between;
	align-items: center;
}
.design-files ul li::before{
	content: '';
    position: absolute;
    top: 18px;
    left: 0;
    width: 6px;
    height: 6px;
    background-color: #000;
    border-radius: 100%;
}
p.item-text{
	font-family: Nunito;
	font-style: normal;
	font-weight: 300;
	font-size: 14px;
	line-height: 180%;
	letter-spacing: 0.01em;
	color: #283441;
}
.item-text.mobile-toast{
	padding: 10px 15px;
	background: #EAF5FF;
	border: 1px solid #2E9BFF;
	box-sizing: border-box;
	box-shadow: 0px 10px 50px rgba(35, 48, 73, 0.05);
	border-radius: 5px;
	margin-top: 20px;
}
@media (max-width: 767px){
	.detail-item{
		margin-bottom: 30px;
	}
}
</style>