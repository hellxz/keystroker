<template>
<div id="wrapper" @keyup.115="loadArticle" @keyup.114="restroke" @keyup.116="changeQqGroup">
    <div id="menu-bar">
        <div id="menu-btn" @click="openMenu">菜单</div>
        <div id="load-article-btn" @click="loadArticle">载文</div>
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
            <label id="cur-speed">220</label>
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
                <div id="control-area"  readonly>
                  <!--当还没开始打字的时候，展示载文-->
                  <!-- <div v-html="textSpans"></div> -->
                  <div id="article-block" v-html="article"></div>
                  <!-- <span class="type-err">在</span><span class="type-suc">工</span><span class="type-suc">作</span><span class="type-err">或</span><span class="type-n">学</span> -->
                  <!--
                    在工作或学习中遇到不开心的时候，不妨静下来好好想想，自己到底是对是错。生活中不是你对别人好，别人就该对你好，你要明白这个道理，每个人都有自己的原则，有人功利，有人善良，你不可能要求别人什么。有时间的话，不妨到处走走，在雄伟的高山之间，放声大喊，一吐心中的阴郁，在浪漫的大海之间，看潮起潮落，感悟人生的起伏跌宕，在落日余晖中感受天地的宁静，洗涤心中的贪念。当你遭遇失恋的时候，不要太悲伤，失去的并非能忘记，拥有的并非不会失去。那些缘来缘去都只是人生的一个瞬间，而人生里那些大段的时间，你会和那个懂你，爱你，珍惜你的人一起度过，好好珍惜在你身边默默陪着你的人。每个人都懂得这个道理，可是还是有人执迷不悟，苦苦执着于那个无缘的人，不肯放手，伤了自己，苦了别人。爱他或她就让那份美好的记忆藏在心底，我们都是在爱的挫折中，逐渐成长起来，才知道什么是爱，又该怎样去爱。希望多年以后再次相遇，还能洒脱的说一句，谢谢你曾经爱过我。当你的婚姻出现问题的时候，多些宽容，多些理解，少些责骂。婚姻本来就是两个人的事，一味的埋怨对方，根本不能解决任何问题。多想想曾经的美好回忆，想想两人同吃一碗面的艰难日子，想想曾经心里的感动。试着做一下换位思考，自己错在哪里，多给自己，也给对方一些机会，人都会有缺点，错误，多些包容，你会活得更轻松。如果真的缘尽了，不妨轻轻的放开手，让彼此都留下美好的回忆，道一声珍重再见，如果不能做朋友，也不可能做敌人，就做那个熟悉的陌生人吧。毕竟生活还是要继续，我们还要继续寻找那个有缘之人。当你和孩子出现问题的时候，不妨想想自己的青春年少，想想那些无知的轻狂岁月，我们都是从年轻走过来的。试着去了解今天的孩子想的什么，喜欢什么，当你以一个朋友的身份去了解他们的时候，你就已经是他们的朋友了，多些沟通，多些理解，多些包容，他们才会向你倾诉他们的烦恼，困惑，迷茫。人生不是十全十美，当你的心觉得累了的时候，不妨为自己的心找一个出口。换一个工作，换一种生活，也换一种对待生活的态度。
                  -->
                </div>
            </div>
            <div slot="bottom" class="split-pane">
                <textarea id="follow-stroke-area" @keyup="stroking" v-model="inputText"></textarea>
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
import $ from 'jquery'
export default {
  name: 'main-page',
  created () {
    document.onkeydown = function (e) {
      var key = window.event.keyCode
      if (key === 114) {
        console.log('F3被按下，用于重打')
      }
    }
  },
  components: {},
  data () {
    return {
      // 设置上打字区域的默认比例
      split2: 0.7,
      isStroking: true,
      currentSegment: 0, // 当前输入到第几段
      strokedSum: 0, // 已打字数
      defaultSplitSegmentSum: 30, // 默认文章字数分段数量
      // article: '在工作或学习中遇到不开心的时候，不妨静下来好好想想，自己到底是对是错。生活中不是你对别人好，别人就该对你好，你要明白这个道理，每个人都有自己的原则，有人功利，有人善良，你不可能要求别人什么。有时间的话，不妨到处走走，在雄伟的高山之间，放声大喊，一吐心中的阴郁，在浪漫的大海之间，看潮起潮落，感悟人生的起伏跌宕，在落日余晖中感受天地的宁静，洗涤心中的贪念。当你遭遇失恋的时候，不要太悲伤，失去的并非能忘记，拥有的并非不会失去。那些缘来缘去都只是人生的一个瞬间，而人生里那些大段的时间，你会和那个懂你，爱你，珍惜你的人一起度过，好好珍惜在你身边默默陪着你的人。每个人都懂得这个道理，可是还是有人执迷不悟，苦苦执着于那个无缘的人，不肯放手，伤了自己，苦了别人。爱他或她就让那份美好的记忆藏在心底，我们都是在爱的挫折中，逐渐成长起来，才知道什么是爱，又该怎样去爱。希望多年以后再次相遇，还能洒脱的说一句，谢谢你曾经爱过我。当你的婚姻出现问题的时候，多些宽容，多些理解，少些责骂。婚姻本来就是两个人的事，一味的埋怨对方，根本不能解决任何问题。多想想曾经的美好回忆，想想两人同吃一碗面的艰难日子，想想曾经心里的感动。试着做一下换位思考，自己错在哪里，多给自己，也给对方一些机会，人都会有缺点，错误，多些包容，你会活得更轻松。如果真的缘尽了，不妨轻轻的放开手，让彼此都留下美好的回忆，道一声珍重再见，如果不能做朋友，也不可能做敌人，就做那个熟悉的陌生人吧。毕竟生活还是要继续，我们还要继续寻找那个有缘之人。当你和孩子出现问题的时候，不妨想想自己的青春年少，想想那些无知的轻狂岁月，我们都是从年轻走过来的。试着去了解今天的孩子想的什么，喜欢什么，当你以一个朋友的身份去了解他们的时候，你就已经是他们的朋友了，多些沟通，多些理解，多些包容，他们才会向你倾诉他们的烦恼，困惑，迷茫。人生不是十全十美，当你的心觉得累了的时候，不妨为自己的心找一个出口。换一个工作，换一种生活，也换一种对待生活的态度。',
      article: '',
      articleArr: [], // 文章分词后的数组，用于查询使用
      textSpans: '',
      keyInputSum: 0,
      inputText: ''
    }
  },
  watch: {
    inputText: function () {
      this.checkTrue()
    },
    isStroking: function () {
      console.log('当前跟打状态为：' + this.isStroking)
      if (this.isStroking === true) {
        $('#control-area').css('overflow', 'hidden')
      } else {
        $('#control-area').css('overflow', 'auto')
      }
    }
  },
  methods: {
    open (link) {
      this.$electron.shell.openExternal(link)
    },
    openMenu () {
      alert('打开设置窗口')
    },
    loadArticle () {
      console.log('从剪贴板载文')
      $('#article-block').html()
      this.article = ''
      this.isStroking = true
      const { clipboard } = require('electron')
      console.log(clipboard.readText('selection'))
      this.article = clipboard.readText('selection')
      this.articleArr = this.article.split('') // 整篇文章转成数组
      let spansContact = ''
      let currentTypeArr = this.articleArr.splice(0, this.defaultSplitSegmentSum)
      for (var i in currentTypeArr) {
        spansContact += '<span class="type-n">' + currentTypeArr[i] + '</span>'
      }
      console.log(spansContact)
      this.textSpans = spansContact
      this.strokeAreaText = '' // TODO 清空操作暂未生效
    },
    sendArticle () {
      $('#article-block').html()
      this.article = ''
      this.isStroking = false
      // 以下是临时测试用，正式时使用数据库或文件内数据
      let xindechukou = '在工作或学习中遇到不开心的时候，不妨静下来好好想想，自己到底是对是错。生活中不是你对别人好，别人就该对你好，你要明白这个道理，每个人都有自己的原则，有人功利，有人善良，你不可能要求别人什么。有时间的话，不妨到处走走，在雄伟的高山之间，放声大喊，一吐心中的阴郁，在浪漫的大海之间，看潮起潮落，感悟人生的起伏跌宕，在落日余晖中感受天地的宁静，洗涤心中的贪念。当你遭遇失恋的时候，不要太悲伤，失去的并非能忘记，拥有的并非不会失去。那些缘来缘去都只是人生的一个瞬间，而人生里那些大段的时间，你会和那个懂你，爱你，珍惜你的人一起度过，好好珍惜在你身边默默陪着你的人。每个人都懂得这个道理，可是还是有人执迷不悟，苦苦执着于那个无缘的人，不肯放手，伤了自己，苦了别人。爱他或她就让那份美好的记忆藏在心底，我们都是在爱的挫折中，逐渐成长起来，才知道什么是爱，又该怎样去爱。希望多年以后再次相遇，还能洒脱的说一句，谢谢你曾经爱过我。当你的婚姻出现问题的时候，多些宽容，多些理解，少些责骂。婚姻本来就是两个人的事，一味的埋怨对方，根本不能解决任何问题。多想想曾经的美好回忆，想想两人同吃一碗面的艰难日子，想想曾经心里的感动。试着做一下换位思考，自己错在哪里，多给自己，也给对方一些机会，人都会有缺点，错误，多些包容，你会活得更轻松。如果真的缘尽了，不妨轻轻的放开手，让彼此都留下美好的回忆，道一声珍重再见，如果不能做朋友，也不可能做敌人，就做那个熟悉的陌生人吧。毕竟生活还是要继续，我们还要继续寻找那个有缘之人。当你和孩子出现问题的时候，不妨想想自己的青春年少，想想那些无知的轻狂岁月，我们都是从年轻走过来的。试着去了解今天的孩子想的什么，喜欢什么，当你以一个朋友的身份去了解他们的时候，你就已经是他们的朋友了，多些沟通，多些理解，多些包容，他们才会向你倾诉他们的烦恼，困惑，迷茫。人生不是十全十美，当你的心觉得累了的时候，不妨为自己的心找一个出口。换一个工作，换一种生活，也换一种对待生活的态度。'
      this.articleArr = xindechukou.split('')
      this.articleArr.forEach(v => {
        this.article += '<span class="type-n">' + v + '</span>'
      })
    },
    changeQqGroup () {
      alert('换群')
    },
    sendScore () {
      alert('发送成绩')
      let score = '复制发送成绩'
      const { clipboard } = require('electron')
      clipboard.writeText(score, 'selection')
    },
    showHistory () {
      alert('跟打历史')
    },
    showKeyboardShotcuts () {
      alert('快捷键展示')
    },
    help () {
      alert('帮助')
    },
    stroking (event) {
      this.isStroking = true
      // 除了需要判断开始跟打外，还要判断是不是输入了特殊的字符
      this.keyInputSum += 1 // 记录击键数
      if (event.keyCode === 8) {
        // console.log($('#article-block').children())
        // console.log('当前输入长度为' + this.inputText.length + '， 当前位置+1的值' + $('#article-block').children()[this.inputText.length])
        for (let index = this.inputText.length; index < $('#article-block').children().length; index++) {
          let deletedChar = $('#article-block').children()[index]
          $(deletedChar).removeClass()
          $(deletedChar).addClass('type-n')
        }
      }
    },
    checkTrue () {
      // $($('#article-block .type-next')[0]).text() // 输出当前第一人未输入的字
      console.log(this.articleArr)
      let inputArr = this.inputText.split('')
      for (let i = 0; i < this.articleArr.length; i++) {
        if (i >= inputArr.length) {
          return
        }
        // 每次遍历都会将错误的文字
        if (this.articleArr[i] !== inputArr[i]) {
          console.log('错误的字是：' + this.articleArr[i] + ' 你的输入是：' + inputArr[i])
          console.log('查看错误的span原class:' + $($('#article-block').children()[i]).attr('class'))
          let originClassName = $($('#article-block').children()[i]).attr('class')
          if (originClassName !== 'type-n' || originClassName !== 'type-suc') {
            $($('#article-block').children()[i]).removeClass()
            $($('#article-block').children()[i]).addClass('type-err')
            console.log('改错误状态')
          }
        } else {
          // 正确的添加成功的标识
          $($('#article-block').children()[i]).removeClass()
          $($('#article-block').children()[i]).addClass('type-suc')
        }
      }
    },
    restroke () {
      console.log('重打')
      // 如果this.article有值，就遍历把所有class不为type-n的改过来
      // 无值就弹窗提示值不存在
      this.sendArticle()
    }
  },
  destroyed () {
    alert('执行保存参数操作')
  }
}
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Source+Sans+Pro");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#wrapper {
  position: absolute;
  left: 0px;
  top: 0px;
  right: 0px;
  bottom: 0px;
  padding-left: 10px;
  padding-right: 10px;
  min-width: 895px;
  min-height: 400px;
  font-family: "思源黑体", "Source Sans Pro", sans-serif;
  line-height: 1;
  font-size: 1.14rem;
  background-color: rgba(233, 233, 216, 1)
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
  color: blue;
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
  color: #000;
}

.split-pane div {
  background-color: #ddd;
}

#control-area {
  width: 100%;
  height: 100%;
  outline: 0 none;
  border-color: rgba(248, 9, 69, 0.8);
  overflow: auto; /* hidden; */
  box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.1), 0 0 8px rgba(248, 9, 69, 0.6);
  resize: none;
}

.type-err {
  color: white;
  background-color: red;
}

.type-suc {
  color: green;
  background-color: darkgrey;
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
