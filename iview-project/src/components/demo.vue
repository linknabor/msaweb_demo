<template>
	<div class="haha">
	<Row>
	<Table :columns="columns" :data="dataList" style="width: 100%;"></Table>
	</Row>
</div>
</template>

<script>
	export default{
		data(){
			return{
				columns:[
				{
                   type:'index',
                   title:'序号',
                   width:60
					
				},
				{
					title:'订单号',
					key:'id',
					align:'center'
				},
				{
				   title:'用户名',
				   key:'user'
				},
				{
					title:'详情',
					key:'show',
					render:(h,params) => {
						return h('Button',{
							props:{
								type:'text',
								size:'small',
							},
							on:{
								click:()=> {
									let ag={id:params.row.id,
									user:params.row.user
									};
									this.$router.push({
										name:'child',
										params:ag
									});
								}
							}
						},'了解详情');
					}
				}
				],
				
				dataList:[
				{
					id:'001',
					user:'小李'
				},
				{
					id:'002',
					user:'小王'
				},
				{
					id:'003',
					user:'小明'
				},
				{
					id:'004',
					user:'小白'
				},
				
				]
			}
		}
	}
</script>

<style lang="less">
	
</style>