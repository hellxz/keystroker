<template>
<div id="wrapper">
    <div id="menu-bar">
        <div id="menu-btn" @click="openMenu">菜单</div>
        <div id="load-article-btn" @click="showLoadPanel">载文</div>
        <div id="send-article-btn" @click="sendArticle">发文</div>
        <div id="switch-qgroup-btn" @click="changeQqGroup">换群</div>
        <div id="send-score-btn" @click="sendScore">发送成绩</div>
        <div id="history-record-btn" @click="showHistory">历史记录</div>
        <div id="keyboard-shortcuts-btn" @click="showKeyboardShotcuts">快捷键</div>
        <div id="help-btn" @click="help">帮助</div>
    </div>
    <div id="tips-label">
        <div>
            当前速度:
            <label id="cur-speed"><bold>220</bold></label>
        </div>
        <div>
            击键:
            <label id="cur-stroke">8.3</label>
        </div>
        <div>
            码长:
            <label id="key-length">2.3</label>
        </div>
        <div>
            平均击键:
            <label id="svg-stroke">8.1</label>
        </div>
        <div>
            平均码长:
            <label id="svg-key-length">2.4</label>
        </div>
    </div>

    <div class="textarea-split">
        <Split v-model="split2" mode="vertical">
            <div slot="top" class="split-pane" >
                <textarea id="control-area" placeholder="对照区 \n按F3载文" readonly>{{this.article}}</textarea>
            </div>
            <div slot="bottom" class="split-pane">
                <textarea id="follow-stroke-area">在工作或学习中遇到不开心的时候，</textarea>
            </div>
        </Split>
    </div>

    <div id="msg-tips">
        <div>
            <label>当前QQ群</label>:
            <label id="cur-qqgroup">指爱/提速</label>
        </div>
        <div>
            <label>段号</label>:第
            <label id="paragraph-no">999</label>段
        </div>
        <div>
            <label>标题</label>:
            <label id="article-title">心的出口</label>
        </div>
        <div>
            <label>总字数</label>:
            <label id="total-words">839</label>字
        </div>
        <div>
            <label>当前进度</label>:
            <label id="cur-rate">3</label>％
        </div>
        <div>
            <label>编码提示</label>:
            <label id="encoding-prompt">不妨givy</label>
        </div>
        <div>
            <label>当前编码</label>:
            <label id="cur-encoding">五笔86</label>
        </div>
    </div>
</div>
</template>

<script>

export default {
  name: 'main-page',
  created () {
    document.onkeydown = function (e) {
      var key = window.event.keyCode
      if (key === 114) {
        console.log('F3被按下，用于重打')
      }
      if (key === 115) {
        console.log('F4被按下，用于载文')
      }
      if (key === 116) {
        console.log('F5被按下，用于换群')
      }
    }
  },
  components: {},
  data () {
    return {
      // 设置上打字区域的比例
      split2: 0.7,
      article: '在工作或学习中遇到不开心的时候，不妨静下来好好想想，自己到底是对是错。生活中不是你对别人好，别人就该对你好，你要明白这个道理，每个人都有自己的原则，有人功利，有人善良，你不可能要求别人什么。有时间的话，不妨到处走走，在雄伟的高山之间，放声大喊，一吐心中的阴郁，在浪漫的大海之间，看潮起潮落，感悟人生的起伏跌宕，在落日余晖中感受天地的宁静，洗涤心中的贪念。当你遭遇失恋的时候，不要太悲伤，失去的并非能忘记，拥有的并非不会失去。那些缘来缘去都只是人生的一个瞬间，而人生里那些大段的时间，你会和那个懂你，爱你，珍惜你的人一起度过，好好珍惜在你身边默默陪着你的人。每个人都懂得这个道理，可是还是有人执迷不悟，苦苦执着于那个无缘的人，不肯放手，伤了自己，苦了别人。爱他或她就让那份美好的记忆藏在心底，我们都是在爱的挫折中，逐渐成长起来，才知道什么是爱，又该怎样去爱。希望多年以后再次相遇，还能洒脱的说一句，谢谢你曾经爱过我。当你的婚姻出现问题的时候，多些宽容，多些理解，少些责骂。婚姻本来就是两个人的事，一味的埋怨对方，根本不能解决任何问题。多想想曾经的美好回忆，想想两人同吃一碗面的艰难日子，想想曾经心里的感动。试着做一下换位思考，自己错在哪里，多给自己，也给对方一些机会，人都会有缺点，错误，多些包容，你会活得更轻松。如果真的缘尽了，不妨轻轻的放开手，让彼此都留下美好的回忆，道一声珍重再见，如果不能做朋友，也不可能做敌人，就做那个熟悉的陌生人吧。毕竟生活还是要继续，我们还要继续寻找那个有缘之人。当你和孩子出现问题的时候，不妨想想自己的青春年少，想想那些无知的轻狂岁月，我们都是从年轻走过来的。试着去了解今天的孩子想的什么，喜欢什么，当你以一个朋友的身份去了解他们的时候，你就已经是他们的朋友了，多些沟通，多些理解，多些包容，他们才会向你倾诉他们的烦恼，困惑，迷茫。人生不是十全十美，当你的心觉得累了的时候，不妨为自己的心找一个出口。换一个工作，换一种生活，也换一种对待生活的态度。'
    }
  },
  methods: {
    open (link) {
      this.$electron.shell.openExternal(link)
    },
    openMenu () {
      alert('打开设置窗口')
    },
    showLoadPanel () {
      alert('载文')
    },
    sendArticle () {
      alert('发文')
    },
    changeQqGroup () {
      alert('换群')
    },
    sendScore () {
      alert('发送成绩')
    },
    showHistory () {
      alert('跟打历史')
    },
    showKeyboardShotcuts () {
      alert('快捷键展示')
    },
    help () {
      alert('帮助')
    }
  }
}
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Source+Sans+Pro");

* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    background-color: lightgray;
}

#wrapper {
    position: absolute;
    left: 10px;
    top: 0px;
    right: 10px;
    bottom: 0px;
    min-width: 895px;
    min-height: 400px;
    font-family: "微软雅黑", "思源黑体", "Source Sans Pro", sans-serif;
    line-height: 1;
    font-size: 1.14rem;
}

#menu-bar {
    position: relative;
    margin-bottom: 2.25rem;
}

#menu-bar div {
    position: relative;
    display: inline;
    padding-left: 0.42rem;
    padding-right: 0.42rem;
    font-size: 1rem;
    color: #000;
}

#menu-bar div:first-child {
    padding-left: 0;
}

#tips-label {
    position: relative;
    margin-bottom: 2rem;
}

#tips-label div {
    position: relative;
    display: inline;
    margin-right: 0.83rem;
    color: lightslategray;
    border: springgreen solid thin;
    border-radius: 8px;
    padding: 15px 10px;
    box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.1), 0 0 8px rgba(98, 238, 16, 0.6);
}

.textarea-split{
    position: fixed;
    left: 10px;
    right: 10px;
    top: 6.3rem;
    font-size: 30px;
    bottom: 30px;
    border: 1px solid #dcdee2;
    line-height: normal;
    font-size: 2rem;
}
.split-pane{
    width: 100%;
    height: 100%;
}

#control-area {
    width: 100%;
    height: 100%;
    outline: 0 none;
    border-color: rgba(248, 9, 69, 0.8);
    overflow: visible;
    box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.1), 0 0 8px rgba(248, 9, 69, 0.6);
    resize: none;
}

#follow-stroke-area {
    width: 100%;
    height: 100%;
    outline: 0 none;
    border-color: rgba(82, 168, 236, 0.8);
    box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.1), 0 0 8px rgba(82, 168, 236, 0.6);
    resize:none;
    overflow: hidden;
}

#msg-tips {
    position: fixed;
    bottom: 10px;
    font-size: 1rem;
    height: 1rem;
}

#msg-tips div {
    position: relative;
    display: inline-table;
    margin-right: 0.5rem;
}

#encoding-prompt {
    color: red
}
</style>
