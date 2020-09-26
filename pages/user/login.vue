<template>
	<view>
		<view class="login-logo"><image src="../../static/common/app_log.png" mode="widthFix"></image></view>
		<view class="login-box">
				<view class="lb-col lb-phone">
					<input type="text" placeholder="请输入手机号" @input="inputNum"/>
				</view>
				<view class="lb-col lb-paswd">
					<input type="text" :password="paswd" @input="passwordNum" placeholder="请输入密码" />
					<button type="default" class="see" :class="paswd?'':'on'" @click="changePaswd"></button>
				</view>
				<navigator class="lb-link" url="/pages/user/changePaswdOne" hover-class="none">忘记密码</navigator>
				<view class="lb-btn"><button type="default" form-type="submit" class="greenBtn" @click="regFun">登 录</button></view>
				<view class="lb-reg">没有账号？<navigator url="/pages/user/register" hover-class="none">立即注册</navigator></view>
			
		</view>
	</view>
</template>

<script>
	
	export default {
		data() {
			return {
				paswd: true,
				uname:'',
				password:'',
			}
		},
		methods: {
			changePaswd: function(e){
				this.paswd = !this.paswd
			},
			inputNum: function(event) {
				this.uname = event.target.value
			},
			passwordNum: function(event) {
				this.password = event.target.value
			},
			
			regFun:function(){
				
				var that = this;
				/*
				uni.request({
					url:that.websiteUrl+'api/user/login/login.html',
					method:"POST",
					data:{
						username:that.uname,
						password:that.password,
					},
					success: (data) => {
						if (data.data.code == 1) { 
							console.log(data.data.data);
							uni.showToast({
							  title: '登录成功!',
							  icon: 'success',
							  duration: 1000
							});
							uni.setStorageSync('login', '1');
							uni.setStorageSync('uphone', data.data.data.uphone);
							uni.setStorageSync('uid', data.data.data.id);
							uni.switchTab({
							  url: '/pages/index/index',
							});                    
						} else{
							uni.showModal({
								title: '温馨提示',
								content: data.data.msg,
								showCancel:false,
							})
						}
					}
				})
				*/
			},
		}
	}
</script>

<style>
.login-logo{
	text-align: center;
	margin: 120upx 0 90upx;
}
.login-logo image{
	width: 230upx;
}
.login-box{
	width: 560upx;
	margin: 0 auto;
}
.login-box .lb-col{
	width: 100%;
	height: 86upx;
	border-bottom: 1px solid #e6e6e6;
	margin-bottom: 40upx;
	position: relative;
}
.login-box .lb-col input{
	display: block;
	width: 100%;
	height: 70upx;
	line-height: 70upx;
	padding: 0 60upx;
	box-sizing: border-box;
	margin-top: 5upx;
	font-size: 28upx;
}
.login-box .lb-col.lb-phone input{
	background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACgAAAAoCAYAAACM/rhtAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAA3ZpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMC1jMDYwIDYxLjEzNDc3NywgMjAxMC8wMi8xMi0xNzozMjowMCAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wTU09Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9tbS8iIHhtbG5zOnN0UmVmPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvc1R5cGUvUmVzb3VyY2VSZWYjIiB4bWxuczp4bXA9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC8iIHhtcE1NOk9yaWdpbmFsRG9jdW1lbnRJRD0ieG1wLmRpZDoxMjE1NjE5MS1iMTNjLWVlNDItOGM1YS1lNmUyMzkzOWMyZGIiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6OTkyMTUzQjg1QzI4MTFFQTlBNDRGMUExQjY3Q0FCNzkiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6OTkyMTUzQjc1QzI4MTFFQTlBNDRGMUExQjY3Q0FCNzkiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIDIwMTUgKFdpbmRvd3MpIj4gPHhtcE1NOkRlcml2ZWRGcm9tIHN0UmVmOmluc3RhbmNlSUQ9InhtcC5paWQ6YmUzZTk5N2ItNTIyNy1iMTRkLThiZTAtM2YyOTM2ZTNiOWZlIiBzdFJlZjpkb2N1bWVudElEPSJ4bXAuZGlkOjEyMTU2MTkxLWIxM2MtZWU0Mi04YzVhLWU2ZTIzOTM5YzJkYiIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PhxZ5xcAAAM/SURBVHja7JhZSFRxFMZnbJAeIlsfsqiosCIKagrUl6IFWk0iomjPl2iBoBclSwiyghbayKAsaaUFQ2wTBIWMokbESNugUtoLooLUzOk78A0cbrPc/9U7+TAHfsy5d+6d+e65/7Pc6w0Gg57ubEmebm4JgQmB/9t81h2BQMDk/BSwAmSA8WAQaAJ14D4oBh0mP+j3+6MLNLAtIB/0t+wfKP8DckAuudplEbRpZ8Bqtf0cPAbfKXgySAUjwRWwixcTF4HHlLgfYCM4azkmGWwC+7m9DbwCp9xOkulgA/1GkBZGnFgbOAAmgF/cdxKMcFvgPn62UOyHGMfLbV+gtgvdFDgaTKR/3Ia4kFWCCvqzTYNicvAk5ZcbBqJYlaUMtwQOUH6jocBm5Y9yK4vblN/LUKBX+Xq+W8ZECn3fgUZxB8W62onAt8qXH31hcO445dfxcxa4EObYPH1BJgIfsG3JslgHrhl2HbF3oJ7+MyCRGqqiLL9f6/QWfwYXwXIwF8wBt2ycJ0V6LP3Tar/07GmxerHXOvLHGBaGsyOItbPG3Y5yfA4LtNhXMBi0gjFsf71VIfdyfVZC5CGnre41WMnu4WMEi0AJpxexHlxfa8ESde5MigtFdVGE/5CLdixQ7BzLxnXQB6wnb9ib+3FQCFk9C/R7tW8Pa2IqI/hNrcGqzg4LmSy21sfBYRGO/8kerAU+AVmWMiRa2nF7g04L9VRQBmrAbtBXrcWXzL6HoIEJpS/oLnjKSFtNJpwv4JOsU+RAqZMkKWR98qhh4TJbXg3Lh7aeIB3M4JrV0b0HsnkRyWpd6ky2XQd9HDizud3KGe8w+BjlvBauJaGAyVLA7M3klDMfPAJTwFKK/Q1umESwVk0w1YxGcyceE3aC7Wo7nQ0gYh2MtgbLlbjzLKqdESe2A6xR21WWIcT2NCPj+jz6ZXxy6yorUckia/WmqcAh4Ah9ybyFLjzungB76csa3Gwi8Kjys1x8Js9lcRc7GOluJlkSJEVFrNRwpHIqMtQeV9mJoH7Wzfe4b5dUFPPClT2rwK1qbmuI0+uX0AiWxtcnUUf+P2z4RXF8PyQJs5g9u+mfZ4XEK+CEwITA6PZXgAEANzbKV5g++9IAAAAASUVORK5CYII=) no-repeat left center;
	background-size: 40upx;
}
.login-box .lb-col.lb-paswd{
	margin-bottom: 0;
}
.login-box .lb-col.lb-paswd input{
	background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACgAAAAoCAYAAACM/rhtAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAA3ZpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMC1jMDYwIDYxLjEzNDc3NywgMjAxMC8wMi8xMi0xNzozMjowMCAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wTU09Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9tbS8iIHhtbG5zOnN0UmVmPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvc1R5cGUvUmVzb3VyY2VSZWYjIiB4bWxuczp4bXA9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC8iIHhtcE1NOk9yaWdpbmFsRG9jdW1lbnRJRD0ieG1wLmRpZDoxMjE1NjE5MS1iMTNjLWVlNDItOGM1YS1lNmUyMzkzOWMyZGIiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6OTk0NDZDMUM1QzI4MTFFQTlBNDRGMUExQjY3Q0FCNzkiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6OTk0NDZDMUI1QzI4MTFFQTlBNDRGMUExQjY3Q0FCNzkiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIDIwMTUgKFdpbmRvd3MpIj4gPHhtcE1NOkRlcml2ZWRGcm9tIHN0UmVmOmluc3RhbmNlSUQ9InhtcC5paWQ6YmUzZTk5N2ItNTIyNy1iMTRkLThiZTAtM2YyOTM2ZTNiOWZlIiBzdFJlZjpkb2N1bWVudElEPSJ4bXAuZGlkOjEyMTU2MTkxLWIxM2MtZWU0Mi04YzVhLWU2ZTIzOTM5YzJkYiIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PgrLc0AAAAJ/SURBVHja7JhNSJRBGMd9SxNLQiiRzItgkdIh2EhBsSBCUesQQQThSQShQEOEgkQ9eLPEg0bYwYOnFG+ieJLA9LBdIkkIQRFPHvzIb7f1N/AsDNK6777vzu4cHPjzn5l3Pv7z9czzjhMOh9NsDufSLA/WC0z320AwGMyHHoOH4C7IAD/BJJgIBAILftp3/OxBxHVBbSDzlGKfwSuEHiZ1BhE3Cj3Vsn6DeRACN8AdyW8EpVra/Awibgiql+QceM8MTZ0oE4DUDNdI1jRlHhgXSMdVam9JcpxOa2OU/wg1S7KF8r2mT3GX8Baoi1UYQS1Q5KB0IjjdmEAaL4DuSbKPzt1O/zvhy6DM5AyWaPGxOOpNg8hg7psUeEWLr8dRbw/8lfhVkwIdj3XDYn5UODIpUDe2/+KoF9IGFzIpcEOLr7mtxGHa1wa0nVA7yMm9BDWBSlAIbsun72DHZT/nQYXcXEty6ygD/wXxy54Fis36BW4aclbUwSlG5IrXu7hbE/dDjLNfF03twYtiT7PBIKj2KrBReJhRvkzk1LE67epmETfN8yHJEp43sLwzbqxBLIH72hWV6JDjxi6m0uV3kuLya3vqGfRC2lSu/oA1P02IUwfoq3jYT0A/ed1WCETIBejDfz695ds1G2ZQ2bTcKN9SL5C9ptyu2Si3xIIVe1AM+saJvOeI37ZCIELUj3qROBWvwS3yxq14WdBEKvfrU7LfZjKEdw15MhFXzPcS5xgQmOfmRom1xN/AI9CATduE/0gdx4ewA3Bd3nRUWPUj8I28VCm/rd3Qndzq1+UvhzrE1c+K82cp2rZSXtIi6OFwjST88SiZ4ewJ+ExgqsOxAAMA/Y6zVSELAMQAAAAASUVORK5CYII=) no-repeat left center;
	background-size: 40upx;
}
.login-box .lb-col .see{
	position: absolute;
	top: 0;
	right: 0;
	z-index: 3;
	width: 70upx;
	height: 70upx;
	background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACIAAAAaCAYAAADSbo4CAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAA3ZpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMC1jMDYwIDYxLjEzNDc3NywgMjAxMC8wMi8xMi0xNzozMjowMCAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wTU09Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9tbS8iIHhtbG5zOnN0UmVmPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvc1R5cGUvUmVzb3VyY2VSZWYjIiB4bWxuczp4bXA9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC8iIHhtcE1NOk9yaWdpbmFsRG9jdW1lbnRJRD0ieG1wLmRpZDoxMjE1NjE5MS1iMTNjLWVlNDItOGM1YS1lNmUyMzkzOWMyZGIiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6OTk0QzBEM0E1QzI4MTFFQTlBNDRGMUExQjY3Q0FCNzkiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6OTk0QzBEMzk1QzI4MTFFQTlBNDRGMUExQjY3Q0FCNzkiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIDIwMTUgKFdpbmRvd3MpIj4gPHhtcE1NOkRlcml2ZWRGcm9tIHN0UmVmOmluc3RhbmNlSUQ9InhtcC5paWQ6YmUzZTk5N2ItNTIyNy1iMTRkLThiZTAtM2YyOTM2ZTNiOWZlIiBzdFJlZjpkb2N1bWVudElEPSJ4bXAuZGlkOjEyMTU2MTkxLWIxM2MtZWU0Mi04YzVhLWU2ZTIzOTM5YzJkYiIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PtAv3s0AAALxSURBVHja7JdNaJNBEIY3aZImplBCPUgRCzVgqY3iQWsRLbQoGAQhFhQxCkIu0qsiVI8K4jEVD3qQohSkoJeAB1vBg9QeRGIuIuKlFqomhaTmr0njMx+7Ekq+iOAhSBaGnf2ZmXfemW9JHLVaTbXCcKoWGW0gbSBtIG0g/w0QV/0iHo9f8/v9J6rV6hRP/1t5/t1ut5LZ6XRaM2fK6/WqjY0NVS6XlcPhsETG5uamdU/Wck/0zs5OValULBFfLpdrsFAo3OXsXSwWu9mQEYxuEWCcgIssL/3LjDW4M8Vi8T16mBg3bEsDyqMdHR0ZvXyEPEf2Gkcm878FwAgiszA2x9oNOyXkeDMgi1AXwuCVDnyaLFIYzZDBOPsu2Tf0/wkDcgyGH2L3Cf2c2OBngWR3EuelbY/o4CsEHgPARS5fZXsIieIwipMVnLyhN5a0829IDpHfEn5sdzDv5t4hwI6g75Le0ACsOZPJqNHR0R+hUMi+WWkiq7m6u7sl65l8Pn+BgEOmUXHUy3oCkBOGmQZl2Lr3Qb6DUqmUx+5xV1fXWCqVWgoGg8PotYal4UB5PB6ru8lkki2rjugnATKAeh1J4PyLsZEvpW6UOctqPY3NMMH3weaD/v7+J319fVck0Ww2ezCRSLy27RGfz2d9mmQagv64BMHxMxy+YP6I3MHxKSRiPmnun0c/gvl+pJe9s9rdNu4viSJ3w+GwikQi9zmfkhjr6+t7bEuzurpq6LwsrOjaRukL612QbAQs+nYpI2dC96wpiQSEvaRe+5AxAi/kcjm1tramenp6hMHb2CzA/mdbRmhOI9M4u8dWGPkpjs3DJs2Ho0EN8qustzS7NHBBl+2AZlXNz89bPShsMOSd+m7LSN0QtJP1AYQJkzU1H9DNWzaNLLNu3gpAk9IfMFmVjUAgoJaXl1UymbT6UNhp+sQ3eZAUX9DvPYLMEWSEgNNSMhlSPmFTjyhyGDaeGkYEbDqdVnb/GhztvxOtCuSXAAMA7CyU8X1PaQkAAAAASUVORK5CYII=) no-repeat center;
	background-size: 34upx;
	transition: all .3s;
	-webkit-transition: all .3s;
	-moz-transition: all .3s;
}
.login-box .lb-col .see.on{
	background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACIAAAAaCAYAAADSbo4CAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyBpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMC1jMDYwIDYxLjEzNDc3NywgMjAxMC8wMi8xMi0xNzozMjowMCAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNSBXaW5kb3dzIiB4bXBNTTpJbnN0YW5jZUlEPSJ4bXAuaWlkOjk1NzRCRjVGNUMzMzExRUFBNzBERThFMDQ2Q0FERDI2IiB4bXBNTTpEb2N1bWVudElEPSJ4bXAuZGlkOjk1NzRCRjYwNUMzMzExRUFBNzBERThFMDQ2Q0FERDI2Ij4gPHhtcE1NOkRlcml2ZWRGcm9tIHN0UmVmOmluc3RhbmNlSUQ9InhtcC5paWQ6OTU3NEJGNUQ1QzMzMTFFQUE3MERFOEUwNDZDQUREMjYiIHN0UmVmOmRvY3VtZW50SUQ9InhtcC5kaWQ6OTU3NEJGNUU1QzMzMTFFQUE3MERFOEUwNDZDQUREMjYiLz4gPC9yZGY6RGVzY3JpcHRpb24+IDwvcmRmOlJERj4gPC94OnhtcG1ldGE+IDw/eHBhY2tldCBlbmQ9InIiPz7+NZTYAAAF00lEQVR42uxXWYwUVRS9975X3TPTPTNOABkEjSMRE1mCAfTDBEwElQ9IVIgffhCXuCGCicaYiMYlLtEoiTGiYvxw+XAhopgQ9IcIJC4sKhAVUBiiGQYGZu2eqnr1rqeqF2YwIv7x4euu7fatd889d3mvWVXpXBhC58j4H8jpw9ZumJ6s3xX2HSEd6iNlJvZQ8fiKIUPxDPGyECrzRWk6lFtx5EY4FOHoUeWflXQrif8s5uB7o46YHbkEBn2R4snbKGz/tQ4CuqeAnGEYIV1qfPKQkMxCcp+A7GvYfg3wOoHxhHrXT4Fl8TSJlSeTjWaJmruAfnWgyTfK9CLeWZ/Z/DdG/jYYX6U51tNa8DLTG9mQuOSxxJe2GckPGJaqN+nhK5z49IEpaewjjgqNZrhpHgW03CT0kXqzQ5hWQWPbv+SI1I80JMbJyiAx28FHV9KcnxkV8jeR6iYoDNQA+ApeEoY/MeNnrggqowz2NkWFhkWuyLPJcl9AZquoPqySnIGRgb5sDgAgce5lk8hKz3y/5vh1DQxx7EdR5fFJz4LMEbDjHYAYRDtjytaDAFXSgHZqRPMp1lUi/hXbN2GsD4YfcbY6Z/NIIJ2HkJhEhX77NIl50Ofoery4ucp9Pa3EWGIBaz4TXg5Yy3CdBtEvuL6t4vdK2Fahq+b5qcxY4yQ+YLs7Pg+OdZzsb3HPpyTS1JGhGUrIDssNbMxjiaUl3gAEjwicegBQRMpWA8lLrMpOqNwCvxtE9HbkwC4YXURZiMCQNSOnSGNIsZiNodWlbJLnbBjPpbg0OjSNbAu5yL4VtfKa8kX+kzQEtpcpf9RkRWmGHLQCMJHxPQmxfi9syn9gInevOB8C6RhUzDupnBxfhorpSufN9TlKimAQS0l54jhyLY0pRR/bzu51jQPJOsvBDAiG60BMkl/Ixo/VEj+V218Rs0cF2H6ifC/5NJ5c8c8MF2/WUotTH61Q9WEWPdUeKNxp1PyBqlns80Nv1nPE4pSMJ9M9SOb4YDaHT/zjgZhO4921ePyiDsS1dnXY3gnHA+9OUjW0gmZWbuui8PwDNQzZyHdP7pBS21HnykMOPwQ4IglJhbqLYfPxuLVrUjju96yUa6PpUJ4a+8Eou0raCB8FzJPOly8eXTWD532L8puogU7BU9b2YnJkeidS08CY0TXvcruZkweafHAxcuJQmuTc0kBJgabyn749OHHhD6Z//KmWlLLi0FELLq2gLHlNWWdoLOPIt+2o6FS3AfzbbC72T9hiS+eFnpIFGRCT9XagtUiyBLeaTYKkbc553iWeB1Gwy+D37xBPQY68CxLQv/xMaJU4CxkjsSUjOZoQkr8gpZ+4uCe33edP9g42dy/US74bUTXtBzUq9NyBF+ep4dUq1W4Fd9LebQHCNXiKWhyFxWQgtroYxvPouruhdBjX72DTK+uNqKAS+kVaamSqfUeRY8ExoaYfLRX32lc5NtOj5p67qX3/aQ1t7zyKWPcHNlxq1X6qFUKfqbVKSZgaymDGY/EK0mbG+8JcckXe8fXkuQMqhxIjm9lrxkTKnqoZvbynIUn4BVyXx7Z8XXRifCf1tBPNGQlEap2TNkD/Vkz2vlGZBukKyI5l8wBbLhJqCIUcekJiaBjmNpzq66nxdCqUq3Gjlji8eoGorMXtfKgvwvXLzFfWM+5HPnBeF+DFuYHyHsx+D2TFCph0GeA0uSiP9YVU6q0fbEC1tgLVcbTiaSVI/AmOTR5ucVd71o1ntTHKqFX+KlZktpUPmXkNZAeM8rNwYBbANNT6TH1Nobpzlf6ofBWWnpeY9SCWn+dUZJ33NEctuu9/2gZkLunxpDG3QiL3CofxfcbLbTD3KKwetZ4PoIn/Bq0jVPecx2JXciFAXWqdbQOuw1iT3tS8fcMbc9gMhP+4I7FnuZODQX0IKfoEknAmO3M1KuNKJOw0GL2mGoUhnPqxLB7x4tZrE2/xJdmFkCRnY4D//ztxrgL5S4ABANIAsOOvXohnAAAAAElFTkSuQmCC) no-repeat center;
	background-size: 34upx;
}
.login-box .lb-link{
	display: block;
	line-height: 65upx;
	text-align: right;
	margin-bottom: 40upx;
	color: #0fc75a;
	font-size: 26upx;
}
.login-box .lb-btn button{
	margin-bottom: 35upx;
}
.login-box .lb-reg{
	line-height: 36upx;
	color: #333333;
	font-size: 26upx;
	padding: 0 10upx;
}
.login-box .lb-reg navigator{
	color: #0fc75a;
}
</style>
