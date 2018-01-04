<template>

    <div ref="div" v-if="block===true" :ontouchmove="ontouchmove"
         style="left: 0px;top:0px;width:100%;height:100%;position: absolute;overflow:hidden;background: rgba(0,0,0,1)">
        <div style="left: 50%;top: 50%;position: absolute;width: 0px;height: 0px">
            <div v-if="block===true" class="view_blocker_rotate_icon" style="margin-left: -33px;margin-top: -85px">

            </div>
            <div style="color: #fff;height: 20px;width: 500px;text-align: center;margin-top: 20px;margin-left: -250px">
                {{blockMessage}}
            </div>
        </div>
    </div>


</template>
<style scoped>
    .fade-enter-active, .fade-leave-active {
        transition: opacity .3s
    }

    .fade-enter, .fade-leave-to /* .fade-leave-active in below version 2.1.8 */
    {
        opacity: 0
    }
    @keyframes view_blocker_rotate_icon_rotation {
        10% {
            transform: rotate(90deg);
            -webkit-transform: rotate(90deg);
        }
        50% {
            transform: rotate(0deg);
            -webkit-transform: rotate(0deg);
        }
        60% {
            transform: rotate(0deg);
            -webkit-transform: rotate(0deg);
        }
        90% {
            transform: rotate(90deg);
            -webkit-transform: rotate(90deg);
        }
        100% {
            transform: rotate(90deg);
            -webkit-transform: rotate(90deg);
        }
    }

    @-webkit-keyframes view_blocker_rotate_icon_rotation {
        10% {
            transform: rotate(90deg);
            -webkit-transform: rotate(90deg);
        }
        50% {
            transform: rotate(0deg);
            -webkit-transform: rotate(0deg);
        }
        60% {
            transform: rotate(0deg);
            -webkit-transform: rotate(0deg);
        }
        90% {
            transform: rotate(90deg);
            -webkit-transform: rotate(90deg);
        }
        100% {
            transform: rotate(90deg);
            -webkit-transform: rotate(90deg);
        }
    }

    .view_blocker_rotate_icon {
        display: inline-block;
        width: 67px;
        height: 109px;
        background-image: url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAIYAAADaCAMAAABU68ovAAAAXVBMVEUAAAD29vb////x8fH////////x8fH5+fn29vby8vL////5+fn39/f6+vr////x8fH////////+/v7////09PT////x8fH39/f////////////////////x8fH///+WLTLGAAAAHXRSTlMAIpML+gb4ZhHWn1c2gvHBvq1uKJcC6k8b187lQ9yhhboAAAQYSURBVHja7d3blpowFIDhTUIAOchZDkre/zE7ycySrbUUpsRN2/1fzO18KzEqxEVgTiZNfgmmtxRc8iaR8HNe8x4BtjQePKayYCIoyBSgvNNE1AkNSHqZyLqk97EgUCCHBzZ5mkg7ScvIJuIyOyXBRFxgpqWZyGsAZLB1KjsJi8nutHU4JCRbFRH8tmirI9k8Jx2sqNs8K/m0LQkrktO2crgcgXGB4AiTEsB0hJfo9MGgX7CGcYiYwQxmMOOvZwRhBG8tCoMXjBDeXvWCEcHbi14wgCBmMIMZzGAGM5jxETNwzMAxA8cMHDNwzMAxA8cMHDNwzMAxA8cMHDNwzMAxY6E2rUQxnH2tz9cirlJFwFBJedaPnUv0M7++egPDE8iAJcIDmxwH5wwv9vUviw2kLbVO3TJU5uul/EyB0FoLp4x60PdGUd3qPurrWyjGGTc05u+1dcgI7/+tCCPARWGhH7o5Y7RCf+bH9ctXLp6v2BVDxfqz0oPXeSVaNtINo/1SXDv4dck8IIkbhtC2ol+iouEonTBCbYvVMnXOjxww6s/RFrBUpXHh/gw1rHj5d/qhYn9Gpk2FWh6xRBRX5Oj3Znh2Sq49/L6+y8pB26q9GbE2dbA2mVbx6I+7MfBglLCttm73ZQi7AD3iL4HqjFYJHSPRppqaUaJ3ATpGa+ckpGak2hRRMyqjGMkvl+xyFeSMwjAqcsZgGDdyhl0oNTnDN4yenJGZFGxNChP5/Y3efh6SM2rDOJMzboYxkDMqwyjIGcIw6F+io2FU1IxIm1JqRmgXSkvNKNCXeTpGrU0JNSO2c6LIGPgCS8AuDHz9ta0SXWDtxoDRH+MqlbC2Dt2G2JFRadtQZt2qq/orGowdGb2euxYiqWEpVWhTBnszoNAPdStuQwxqf0aocdWKW4Z+DfszIh8pxJqbuCE4YAC+4bm0evtipjpgJHeFnyyt1Ku2xa0bhjxr27p75rECNwyI9ZwvXkHq+7aTaMEV44YYy/spfgjgjNHaWW+GeUhGEX7tLlVinIFDDSgnOwhi1V6bU0b6tVS9eAERe863g4dRrtiHdc6o+nn5vtyVVgR79Cqt4uL6gfHPQyGqtP2vf7HADGbcYwaOGThm4JiBYwaOGThm4JiBYwaOGThm4JiBYwaOGThm4JiBYwaOGThm4JjhtOM+J/AgT008yDMkN/dPP9hzS8zAMQN3OEYeekp5YU7KOKXwVXqiY+QS7smcinGKABWdiBgpPJTSMHJ4KidhhPBUSMLw4CmPhKHgKUXCkHsygum71ftNSgCX6bsl8FQyfbcL5EdYsDk0R3j7aiA5wpt5AjKg/2gLJEBD/0Hf2OOf/vRrj6z/7GtP4B3nMKyjHA12kIPSjnJs3FEO0TvKkYJHOWCR+rjJH0Vn6fI5PjNbAAAAAElFTkSuQmCC');
        transform: rotate(90deg);
        -webkit-transform: rotate(90deg);
        -webkit-animation: view_blocker_rotate_icon_rotation infinite 1.5s ease-in-out;
        animation: view_blocker_rotate_icon_rotation infinite 1.5s ease-in-out;
        -webkit-background-size: 67px;
        background-size: 67px
    }
</style>

<script>
    // 注册
    const LANDSCAPE = 'landscape';
    const PORTRAIT = 'portrait';

    function viewType() {

        if (window.innerWidth > window.innerHeight) {
            return LANDSCAPE
        } else {
            return PORTRAIT
        }
    }

    import JohnnyUtils from 'johnny-utils'

    export default {

        name: 'vue-view-blocker',
        // 声明 props
        props: {
            type: {
                type: String,
                default: PORTRAIT
            },
            blockMessage: {
                type: String,
                default: ''
            },
            scroll:{
                type: Boolean,
                default: false
            }
        },
        data: function () {
            return {
                block: false,
                removeEvent: function () {
                },
                ontouchmove:''
            }
        },
        methods:{
            update:function () {
                switch (this.type) {
                    case LANDSCAPE:
                        if (viewType() === PORTRAIT) {
                            this.block =true;
                        } else {
                            this.block = false;
                        }
                        break;
                    default:
                        if (viewType() === LANDSCAPE) {
                            this.block =true;
                        } else {
                            this.block = false;
                        }
                        break
                }
            }
        },
        beforeDestroy: function () {
            this.removeEvent()
        },
        mounted: function () {
            let self = this;
            this.removeEvent = JohnnyUtils.bindEvent(window, 'resize', function () {
                self.update();
                setTimeout(self.update, 200)
            });
            self.update();
            if (false === this.scroll) {
                this.ontouchmove= 'event.preventDefault();';
            }
        }
    }
</script>