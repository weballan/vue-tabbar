<template>
	<div id="app">
		<transition :name="tranName">
			<router-view class="transitionName">

			</router-view>
		</transition>
		<tab-bar />
	</div>
</template>

<script>
	import TabBar from '@/components/tabbar/TabBar'
	export default {
		name: 'App',
		data(){
			return{
				tranName:''
			}
		},
		watch:{
			'$route'(to,from){
				const toPath=to.path.split('/').length;
				const fromPath=from.path.split('/').length;
				this.tranName=toPath===fromPath?'':(toPath<fromPath)?'slide-right':'slide-left'
			}
		},
		methods:{

		},
		components:{
			TabBar
		}
	}
</script>

