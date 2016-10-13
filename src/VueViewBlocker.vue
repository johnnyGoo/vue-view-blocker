<template>
    <div v-show="display" style="width: 100%;height: 100%;position: absolute;z-index: 99999;left: 0px;top:0px">
        <slot ></slot>
    </div>
</template>


/*!
* vue-view-blocker v0.0.1 (https://github.com/johnnyGoo/vue-view-blocker)
* Author: Johnny chen
*
* Copyright 2013-2016 Johnny chen
*/
<script>


    var count = 0;

    if (!window.Smart) {
        throw 'vue-view-blocker required smart.js'
    }
    var Smart = window.Smart;
    var Css = Smart.Css;
    var _ = Smart._;

    // 注册
    export default {
        // 声明 props
        props: {
            type: {
                type: Number,
                default: 1
            }
        },
        data: function () {
            return {
                display: false
            }

        },
        methods: {},
        computed: {},
        ready: function () {
            var me = this;

            function onresize() {
                var windowSize = Smart.Utils.windowSize();
                if (windowSize.width > windowSize.height) {
                    if (me.type == 1) {
                        me.display = true;
                    }else{
                        me.display = false;
                    }

                } else {
                    if (me.type == 2) {
                        me.display = true;
                    }else{
                        me.display = false;
                    }
                }
            }

            var rm_widow = Smart.Event.windowEvent('resize', onresize);

            onresize();


        }


    }


</script>