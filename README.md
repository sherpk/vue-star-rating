# vue-star-rating
基于vue的评星组件
1.传参        props: {
            score: {
                type: Number,
                default: 0,
                //required: true //可设置为是否必传
            },
            disabled: {
                type: Boolean,
                default: false,//设置是否可以编辑
            },
            showText: {
                type: Boolean,
                default: false,//设置是否显示出分数
            },
        },
        
2.星星样式的font-icon需要引用自己文件的字体图标        
