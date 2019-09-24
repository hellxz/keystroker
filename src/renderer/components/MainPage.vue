<template>
<div id="wrapper"><!--窗口最窄1202px-->
    <div id="menu-bar">
        <div id="menu-btn">菜单</div>
        <div id="load-article-btn">载文</div>
        <div id="send-article-btn">发文</div>
        <div id="switch-qgroup-btn">换群</div>
        <div id="send-score-btn">发送成绩</div>
        <div id="history-record-btn">历史记录</div>
        <div id="keyboard-shortcuts-btn">快捷键</div>
        <div id="help-btn">帮助</div>
    </div>
    <div id="tips-label">
        <div>
            当前速度:
            <label id="cur-speed">500</label>
        </div>
        <div>
            击键:
            <label id="cur-speed">500</label>
        </div>
        <div>
            码长:
            <label id="cur-speed">500</label>
        </div>
        <div>
            平均击键:
            <label id="cur-speed">500</label>
        </div>
        <div>
            平均码长:
            <label id="cur-speed">500</label>
        </div>
    </div>
    <div id="text-viewpoint">
        <div>
            <textarea id="control-area">对照区</textarea>
        </div>
        <div id="control-bar">
            <!--准备放张小图片-->
        </div>
        <div>
            <textarea id="follow-stroke-area">跟打区</textarea>
        </div>
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
  methods: {
    open (link) {
      this.$electron.shell.openExternal(link)
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

body {
  font-family: "微软雅黑", "思源黑体", "Source Sans Pro", sans-serif;
  line-height: 1;
  font-size: 1.38rem;
}

#wrapper {
  position: absolute;
  left: 10px;
  top: 0px;
  right: 10px;
  bottom: 0px;
}

#menu-bar {
    position: relative;
    margin-bottom: 1.25em;
}

#menu-bar div {
  position: relative;
  display: inline-table;
  margin-right: 0.83em;
}

#tips-label {
    position: relative;
    margin-bottom: 2em;
}

#tips-label div {
  position: relative;
  display: inline-table;
  margin-right: 0.5em;
}

#text-viewpoint {
    position: relative;
    width: 100%;
    height: 50%;
    font-size: 30px;
}

#control-area {
    width: 100%;
    height: 48.5%;
    font-size: 3rem;
}

#control-bar {
    width: 100%;
    height: 1%;
}

#follow-stroke-area {
    width: 100%;
    height: 48.5%;
    font-size: 3rem;
}

#msg-tips {
    position: absolute;
    bottom: 5px;
}

#msg-tips div {
  position: relative;
  display: inline-table;
  margin-right: 0.5em;
}

#encoding-prompt {
    color: red
}

.doc button.alt {
  color: #42b983;
  background-color: transparent;
}
</style>
