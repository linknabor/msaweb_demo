<template>
	
	<div class="kk">
		<Table :columns="ccc" :data="dataAg" style="width: 100%;">
			
		</Table>
		<span style="font-size: 30px;">{{total}}</span>
		
	</div>
</template>

<script>
	export default{
		name:'child',
		data(){
			return{
				total:0,
				ccc:[
				{
					title:'编号',
					key:'id',
					align:'center'
				},
				{
					title:'买家',
					key:'user',
					align:'center'
				}
				],
				dataAg:[]
			}
		},
		
		methods:{
			init(){
				
				let order = {
                id: this.$route.params.id,
                user: this.$route.params.user
                
            };
            this.dataAg = [order];
			},
			
			
			
			
			
			
			add(){
				var that=this;
				setInterval(that.addAll,1);
			},
			
			    addAll(){
				var total=0;
				if(this.total<100){
					this.total++;
				}else{
					clearInterval(this.addAll);
				}
			return total
			}
			
		},
		mounted(){
			this.init();
			
			
		},
		activated () {
        this.init();
      
  },
 
 	
				
			created(){
				this.add();
			}
 	
 
 }
  	
			
  
	
</script>

<style scoped>
</style>