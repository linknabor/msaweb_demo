<template>
	<div>
		<section class="master-page-container">
    <div class="master-page-wrap">
        <div class="title-header">
            <div class="title-content">
                <div class="title-icon">
                    <slot name="title-icon"></slot>
                </div>
                <p class="title">{{title}}</p>
            </div>
            <div class="title-toolbar">
                <slot name="title-toolbar"></slot>
            </div>
        </div>
        <div class="master-page-content-toolbar" v-if="$slots.search || $slots.btns">
            <div class="bar-search">
                <slot name="search"></slot>
            </div>
            <div class="bar-group">
                <slot name="btns"></slot>
            </div>
        </div>
        <!--$slots.content表示$slots里面是否存在content内容，就是说这里的占位符可填充了内容-->
        <div class="master-page-content" v-if="$slots.content">
            <slot name="content">    
            </slot>
        </div>
    </div>
</section>
</div>

</template>

<script>
	export default{
		data(){
			return{
				title:{
					type:String
				}
			}
		}
		}
	
</script>

<style lang="less" scoped>
.master-page-container{
    background-color: #fff;
    .master-page-wrap{
        .title-header{
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding:10px 20px;
            border-bottom: 1px solid #dddee1;
            .title-content{
                display: flex;
                align-items: center;
                .title-icon{
                    display: flex;
                    align-items: center;
                    margin-right:5px;
                }
                p.title{
                    font-size: 14px;
                    font-weight: bold;
                }
            }
            .title-toolbar{

            }
        }        
        .master-page-content-toolbar{
            padding: 20px 30px;          
            display: flex;
            align-items: center;
            justify-content: space-between;
            border-bottom:1px solid #dddee1;
            .bar-search{
                .input-search{
                    width:350px;
                }
            }
            .bar-group{

            }
        }
        .master-page-content{
            padding:15px 20px;
            background: #fff;
        }
    }
}
	
</style>