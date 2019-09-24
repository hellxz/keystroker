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
        <div class="text-div">
            <textarea id="control-area" readonly >对照区</textarea>
        </div>
        <div id="control-bar">
            <!--准备放张小图片-->
            …
        </div>
        <div class="text-div">
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
  font-size: 1.14rem;
}

#wrapper {
  position: absolute;
  left: 10px;
  top: 0px;
  right: 10px;
  bottom: 0px;
  min-width: 878px;
  min-height: 500px;
}

#menu-bar {
    position: relative;
    margin-bottom: 1.25rem;
}

#menu-bar div {
  position: relative;
  display: inline-table;
  margin-right: 0.83rem;
}

#tips-label {
    position: relative;
    margin-bottom: 2rem;
}

#tips-label div {
  position: relative;
  display: inline-table;
  margin-right: 0.5rem;
}

#text-viewpoint {
    position: fixed;
    left: 10px;
    right: 10px;
    top: 6.3rem;
    font-size: 30px;
    bottom: 30px;
}

#text-viewpoint .text-div {
    height: 49.5%;
}

#control-area {
    width: 100%;
    height: 100%;
    font-size: 3rem;
    outline: 0 none;
    border-color: rgba(82, 168, 236, 0.8);
    overflow: visible;
    box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.1), 0 0 8px rgba(82, 168, 236, 0.6);
    resize: none;
}

#control-bar {
    width: 100%;
    height: 1%;
    color: rgba(51, 39, 39, 0.521);
    text-align: center;
    line-height: 1px;
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
    bottom: 5px;
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

.doc button.alt {
  color: #42b983;
  background-color: transparent;
}
</style>
