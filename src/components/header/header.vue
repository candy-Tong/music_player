<template>
    <div class="header">
        <div class="background"></div>
        <div class="head">
            <span class="my-music">我的歌单</span>
            <span class="icon-arrow_lift"></span>
            <span class="icon-search"></span>
            <span class="icon-more_vert"></span>
        </div>

        <img src="./avatar.jpg" alt="" class="picture">
        <div class="user-wrapper">
            <span class="title">我喜欢的音乐</span>
            <img src="./avatar.jpg" alt="" class="avatar">
            <span class="name">candyTong</span>
            <span class="icon-keyboard_arrow_right"></span>
        </div>
        <div class="music-wrapper">
            <div v-for="(item,index) in this.music" class="music-item" @click.stop="playMusic(index)">
                <span class="number">{{index+1}}</span>
                <span class="musicName">{{item.name}}</span>
                <span class="singer">{{item.author}}</span>
                <span v-show="item.mvPath" class="icon-play" @click.stop="showMv(index)"></span>
                <span class="icon-keyboard_arrow_right"></span>
            </div>
        </div>
        <div class="audio" v-show="!mvShow">
            <audio :src="music[musicIndex].musicPath" controls="controls" class="music-audio"></audio>
        </div>
        <div class="mv-wrapper" v-show="mvShow">
            <video width="100%" controls="controls" class="mv">
                <source :src="music[1].mvPath">
            </video>
            <span class="icon-close" @click.stop="closeMv"></span>
        </div>
    </div>

</template>

<script type="text/ecmascript-6">

    import $ from 'jquery';
    export default{
        data() {
            return {
                music: [
                    {
                        name: '最后的旅行',
                        author: '绘梨衣',
                        musicPath: require('./最后的旅行.mp3'),
                        imgPath: require('./最后的旅行.jpg')
                    },
                    {
                        name: '告白气球',
                        author: '周杰伦',
                        musicPath: require('./告白气球.mp3'),
//                        imgPath: require('./告白气球.jpg'),
                        mvPath: require('./告白气球.mp4')
                    },
                    {
                        name: '最后的旅行',
                        author: '绘梨衣',
                        musicPath: require('./最后的旅行.mp3'),
                        imgPath: require('./最后的旅行.jpg')
                    }, {
                        name: '最后的旅行',
                        author: '绘梨衣',
                        musicPath: require('./最后的旅行.mp3'),
                        imgPath: require('./最后的旅行.jpg')
                    }, {
                        name: '最后的旅行',
                        author: '绘梨衣',
                        musicPath: require('./最后的旅行.mp3'),
                        imgPath: require('./最后的旅行.jpg')
                    }, {
                        name: '最后的旅行',
                        author: '绘梨衣',
                        musicPath: require('./最后的旅行.mp3'),
                        imgPath: require('./最后的旅行.jpg')
                    }, {
                        name: '最后的旅行',
                        author: '绘梨衣',
                        musicPath: require('./最后的旅行.mp3'),
                        imgPath: require('./最后的旅行.jpg')
                    }, {
                        name: '最后的旅行',
                        author: '绘梨衣',
                        musicPath: require('./最后的旅行.mp3'),
                        imgPath: require('./最后的旅行.jpg')
                    }, {
                        name: '最后的旅行',
                        author: '绘梨衣',
                        musicPath: require('./最后的旅行.mp3'),
                        imgPath: require('./最后的旅行.jpg')
                    }, {
                        name: '最后的旅行',
                        author: '绘梨衣',
                        musicPath: require('./最后的旅行.mp3'),
                        imgPath: require('./最后的旅行.jpg')
                    }, {
                        name: '最后的旅行',
                        author: '绘梨衣',
                        musicPath: require('./最后的旅行.mp3'),
                        imgPath: require('./最后的旅行.jpg')
                    }, {
                        name: '最后的旅行',
                        author: '绘梨衣',
                        musicPath: require('./最后的旅行.mp3'),
                        imgPath: require('./最后的旅行.jpg')
                    }
                ],
                mvShow: false,
                index: -1,
                musicIndex: 0
            };
        },
        methods: {
            showMv(index) {
                this.mvShow = true;
                this.index = index;
                var audio = $('.music-audio')[0];
                var waittime = 1000;
                audio.pause();
                setTimeout(function () {
                    if (audio.paused) {
                        $('.mv').trigger('play');
                    }
                }, waittime);
            },
            closeMv() {
                this.mvShow = false;
                var mv = $('.mv')[0];
                mv.pause();
                var audio = $('.music-audio')[0];
                audio.pause();
                var waittime = 1000;
                setTimeout(function () {
                    if (mv.paused) {
                        audio.play();
                    }
                }, waittime);
            },
            playMusic(index) {
                var audio = $('.music-audio')[0];
                if (this.musicIndex === index && !audio.paused) {
                    return;
                }
                audio.pause();
                this.musicIndex = index;
                console.log(this.musicIndex);
                var waittime = 15;
                setTimeout(function () {
                    if (audio.paused) {
                        audio.play();
                    }
                }, waittime);
            }
        }
    };
    $(document).ready(function () {
//        $('.music-wrapper').height($(window).height() - $('.picture').outerHeight(true) - 48);
        let minheight = $(window).height() - $('.picture').outerHeight(true) - 48;
        $('.music-wrapper').css({minHeight: minheight});
    });
    let minheight = $(window).height() - $('.picture').outerHeight(true) - 48;
    $('.music-wrapper').css({minHeight: minheight});
</script>


<style lang="stylus" rel="stylesheet/stylus">
    @import "../../common/stylus/icon.styl"
    @import "../../common/stylus/mixin.styl"
    .header
        .background
            position absolute
            top 0
            left 0
            width 100%
            height 100%
            z-index -1
            filter blur(10px)
            opacity 0.5
        .head
            position fixed
            top 0
            left 0
            background #999
            height 48px
            width 100%
            line-height 48px
            z-index 100
            opacity 0.5
            .my-music
                line-height 48px
                display inline-block
                text-indent 48px
            .icon-arrow_lift
                position fixed
                width 24px
                height 24px
                top 12px
                left 12px
                line-height 24px
            .icon-search
                position fixed
                width 24px
                height 24px
                top 12px
                right 50px
                line-height 24px
            .icon-more_vert
                position fixed
                width 24px
                height 24px
                top 12px
                right 12px
                line-height 24px
        .picture
            float left
            width 128px
            height 128px
            margin 63px 15px 15px 24px
        .user-wrapper
            float left
            margin 78px 0px 10px 10px
            .title
                display block
                line-height 32px
            .avatar
                line-height 32px
                width 32px
                height 32px
                vertical-align middle
            .icon-keyboard_arrow_right
                line-height 32px
                vertical-align middle
        .music-wrapper
            opacity 0.5
            width 100%
            clear both
            padding-bottom 48px
            border-radius 2px
            background #f5f7f9
            .music-item
                position relative
                width 100%
                height 64px
                border-top solid 1px #9ea7b4
                .number
                    display inline-block
                    float left
                    width 56px
                    height 56px
                    margin 4px
                    line-height 56px
                    font-size 20px
                    text-align center
                .musicName
                    display block
                    height 36px
                    line-height 36px
                    font-size 16px
                    padding-top 2px
                .singer
                    display inline-block
                    height 16px
                    font-size 13px
                .icon-play
                    display inline-block
                    line-height 16px
                    vertical-align middle
                .icon-keyboard_arrow_right
                    position absolute
                    width 56px
                    height 56px
                    line-height 56px
                    text-align center
                    font-size 24px
                    top 4px
                    right 4px
        .audio
            position fixed
            bottom 0
            left 0
            width 100%
            height 48px
            audio
                width 100%
                height 100%
        .mv-wrapper
            position fixed
            top 0
            left 0
            width 100%
            height 100%
            background rgba(101, 113, 128, 0.5)
            z-index 200
            .mv
                display inline-block
                height auto
                margin-top 30%
                width 100%
            .icon-close
                position relative
                margin 0 auto
                display block
                width 32px
                height 32px
                line-height 32px
                text-align center
                font-size 20px

</style>
