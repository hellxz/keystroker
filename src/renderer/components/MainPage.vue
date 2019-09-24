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
            <label id="cur-speed">500</label>
        </div>
        <div>
            击键:
            <label id="cur-stroke">500</label>
        </div>
        <div>
            码长:
            <label id="key-length">500</label>
        </div>
        <div>
            平均击键:
            <label id="svg-stroke">500</label>
        </div>
        <div>
            平均码长:
            <label id="svg-key-length">500</label>
        </div>
    </div>

    <div class="textarea-split">
        <Split v-model="split2" mode="vertical">
            <div slot="top" class="split-pane" >
                <textarea id="control-area" readonly>对照区</textarea>
            </div>
            <div slot="bottom" class="split-pane">
                <textarea id="follow-stroke-area">跟打区</textarea>
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
            <label id="total-words">972</label>字
        </div>
        <div>
            <label>当前进度</label>:
            <label id="cur-rate">1</label>％
        </div>
        <div>
            <label>编码提示</label>:
            <label id="encoding-prompt">lkim</label>
        </div>
        <div>
            <label>当前编码</label>:
            <label id="cur-encoding">五笔86</label>
        </div>
    </div>
</div>
</template>

<script>
//   import SystemInformation from './LandingPage/SystemInformation'

export default {
  name: 'main-page',
  components: {},
  data () {
    return {
      split2: 0.5
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
    },
    changeTextAreaSizeStart (e) {
      console.log(e)
    },
    changeTextAreaSize (e) {
      console.log('拖动完成')
      console.log(e)
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
}
.split-pane{
    width: 100%;
    height: 100%;
}

#control-area {
    width: 100%;
    height: 100%;
    font-size: 3rem;
    outline: 0 none;
    border-color: rgba(248, 9, 69, 0.8);
    overflow: visible;
    box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.1), 0 0 8px rgba(248, 9, 69, 0.6);
    resize: none;
}

#follow-stroke-area {
    width: 100%;
    height: 100%;
    font-size: 3rem;
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
