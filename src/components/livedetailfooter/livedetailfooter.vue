<template>
	<div class="tools">
		<div class="contentfooter">
			<div class="content-cell">
				<div class="course">
					<router-link to="opportunity">
						<img src="../../assets/pinkeNormal.png" class="tools-icon">
						<span class="title">拼课</span>
					</router-link>
				</div>
				<div class="send" @click="showGiveFriend">
					<img src="../../assets/givefrend.png" class="toolse-icon">
					<span class="titlee">送朋友</span>
				</div>
				<div class="price">
					<span class="count">￥1500</span>
				</div>
			</div>		
		</div>
		<transition name="fade">
			<modal v-show="modalshow" @commitAction="commitAction" @hideGiveFriend="hideGiveFriend"></modal>
		</transition>
		<transition name="fade">
			<modal-bank v-show="priceshow" @commitPrice="commitActionPrice" @hidePrice="hidePrice" :totalPrice="pingkeObject.totalPrice" :count="pingkeObject.count"></modal-bank>
		</transition>
	</div>
</template>
<script type="text/javascript">
import modal from '@/components/common/modal';
import modalBank from '@/components/common/modalbank';
export default {
	data () {
		return {
			modalshow: false,
			priceshow: false,
			pingkeObject: {
				type: Object
			}
		};
	},
	methods: {
		showGiveFriend() {
			this.modalshow = true;
		},
		hideGiveFriend() {
			this.modalshow = false;
		},
		hidePrice() {
			this.priceshow = false;
		},
		commitAction(val1, val2) {
			this.modalshow = false;
			this.priceshow = true;
			this.pingkeObject.count = val1;
			this.pingkeObject.totalPrice = val2;
			console.log('做一些提交处理', this.count, this.totalPrice);
		},
		invoicing() {
			this.priceshow = true;
		},
		commitActionPrice() {
			this.priceshow = false;
		}
	},
	components: {
		modal,
		modalBank
	}

};
</script>
<style lang="stylus" scroped>
.tools
	position: fixed
	bottom: 0px
	height: 50px
	width: 100%
	background: white
	.contentfooter
		position: relative
		.content-cell
			display: flex
			.course
				flex: 0 0 30%
				vertical-align: middle
				border-right: 1px solid rgba(7, 17, 27, 0.1)
				border-top: 1px solid rgba(7, 17, 27, 0.1)
				.tools-icon
					position: absolute
					padding-left: 12%
					padding-top: 5px
					width: 20px
					height: 20px
				.title
					position: absolute
					padding-left: 11%
					padding-top: 30px
					font-size: 14px
					color: #333333
				
			.send
				flex: 0 0 30%
				// text-align: center
				height: 50px
				border-top: 1px solid rgba(7, 17, 27, 0.1)
				border-right: 1px solid rgba(7, 17, 27, 0.1)
				.toolse-icon
					position: absolute
					padding-left: 12%
					padding-top: 5px
					width: 20px
					height: 20px
				.titlee
					position: absolute
					padding-left: 9%
					padding-top: 30px
					font-size: 14px
					color: #333333
			.price
				flex: 0 0 40%
				height: 50px
				border-top: 1px solid rgba(7, 17, 27, 0.1)
				background-color: #ef5350;
				.count
					position: absolute
					color: #ffffff
					width: 100%
					height: 60px
					line-height: 20px
					padding-top: 15px
					padding-left: 12%
					font-size: 20px
</style>
