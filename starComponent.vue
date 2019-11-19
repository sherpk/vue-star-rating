<template>
    <span class="rate" :class="{'disabled':disabled}" style="cursor: pointer">
        <i v-for="i in 5" class="iconfont" @mouseenter="disabled?'':curScore=i" @mouseleave="disabled?'':curScore=''" @click="disabled?'':setScore(i)" :class="getClass(i)">
            <i v-if="disabled&&i==Math.floor(score)+1" class="iconfont icon-star" :style="'width:'+width"></i>
        </i>
        <span v-if="showText" class="text">{{curScore||score}}分</span>
    </span>
</template>

<script>
    export default {
        name:'MyRate',
        props: {
            score: {
                type: Number,
                default: 0,
                //required: true
            },
            disabled: {
                type: Boolean,
                default: false,
            },
            showText: {
                type: Boolean,
                default: false,
            },
        },
        data() {
            return {
                curScore: '',
                width:'',
            }
        },
        created: function () {
//            this.getDecimal();
        },
        methods: {
            getClass(i) {
                if (this.curScore === '') {
                    return i <= this.score ?  'aid aid-star gold' : 'aid aid-star-outline'
                } else {
                    return i <= this.curScore ? 'aid aid-star gold' : 'aid aid-star-outline'
                }
            },
            getDecimal() {
                this.width=Number(this.score * 100 - Math.floor(this.score) * 100)+'%';
            },
            setScore(i){
                this.$emit('update:score',i);//使用`.sync`修饰符，对score 进行“双向绑定
            }
        }
    }
</script>
<style lang="scss" scope>
    .gold{
        color: #efcd49;
    }
    .rate {
        i{
            font-size:28px;
        }
    }
</style>
