<script setup lang="ts">
import moment from 'moment'
import {ref} from 'vue'
import 'remixicon/fonts/remixicon.css'

const senders = [
  {icon: '/avatar.jpg', id: 0},
  {icon: '/logo.png', id: 1}
]
const conversations = [
  {
    icon: '/logo.png',
    title: '数翼',
    date: moment().format('LT'),
    messages: [
      {content: '小翼正在为您您服务', date: '9:22 PM', sender: senders[1]},
      {content: '中国的首都在哪里', date: '9:22 PM', sender: senders[0]},
      {content: '北京', date: '9:22 PM', sender: senders[1]},
      {content: '背诵一首唐诗', date: '9:22 PM', sender: senders[0]},
      {
        content:
            '张继《枫桥夜泊》\n' +
            '月落乌啼霜满天，江枫渔火对愁眠。\n' +
            '姑苏城外寒山寺，夜半钟声到客船。',
        date: '9:22 PM',
        sender: senders[1]
      }
    ]
  },
  {
    icon: '/avatar.jpg',
    title: '自言自语',
    date: moment().format('LT'),
    messages: [{content: '小翼正在为您您服务', date: '9:22 PM', sender: senders[1]}]
  }
]
const activeIdx = ref(0)
</script>

<template>
  <div class="toolbar">
    <img class="logo" src="/logo.png" alt=""/>
    <span class="gap"></span>
    <img class="avatar" src="/avatar.jpg" alt=""/>
  </div>
  <div class="toolbox">
    <div class="title">聊天和工具</div>
    <div class="search">
      <input type="text" placeholder="搜索你的对话"/>
    </div>
    <div class="conversations">
      <div
          v-for="(cv, idx) in conversations"
          class="conversation"
          :class="activeIdx == idx ? 'active' : ''"
          @click="activeIdx = idx"
      >
        <img :src="cv.icon" alt=""/>
        <div class="name">{{ cv.title }}</div>
      </div>
    </div>
  </div>
  <div class="chatcontainer">
    <div class="top">
      <img :src="conversations[activeIdx].icon" alt=""/>
      <div class="title">
        <div class="name">{{ conversations[activeIdx].title }}</div>
        <div class="date">{{ conversations[activeIdx].date }}</div>
      </div>
    </div>
    <div class="middle">
      <div
          class="message"
          v-for="message in conversations[activeIdx].messages"
          :class="message.sender.id == 0 ? 'self' : ''"
      >
        <img :src="message.sender.icon" alt=""/>
        <div class="content">{{ message.content }}</div>
        <div class="date">{{ message.date }}</div>
        <div class="gap"></div>
      </div>
    </div>
    <div class="bottom">
      <input type="text"/>
    </div>
  </div>
</template>

<style lang="stylus">
#app {
  display: flex;
  width: 100%;
  height: 100%;
  padding: 0;
  margin: 0;
  border: 0;
}
</style>
<style scoped lang="less">

//theme1
@toolbar-background: linear-gradient(135deg, rgba(240, 47, 194, 0.733), rgba(96, 148, 234, 0.667));
@toolbox-background: linear-gradient(135deg, rgba(151, 150, 240, 0.333), rgba(251, 199, 212, 0.6));
@top-background: #ffffff00;
@bottom-background: linear-gradient(180deg, #ffffff00, #c68ee133);
@active-background: linear-gradient(135deg, rgba(151, 150, 240, 0.7), rgba(251, 199, 212, 0.7));
@container-background: linear-gradient(135deg, rgba(255, 224, 0, 0), rgba(121, 159, 12, 0));
@message-background: rgb(249 250 251);
@message-background2: rgb(249 250 251);
@message-color: rgba(99, 102, 241, 0.76);
@message-color2: #666;

//theme2
@toolbar-background: linear-gradient(135deg, #fccf31, rgba(236, 103, 103, 0.69));
@toolbox-background: linear-gradient(135deg, rgba(253, 216, 81, 0.34), rgba(252, 122, 122, 0.34));
@top-background: #ffffff44;
@bottom-background: linear-gradient(135deg, #ffe98500, #fa742b00);
@active-background: linear-gradient(135deg, #fdde4d, rgba(252, 142, 84, 0.3));
@container-background: linear-gradient(180deg, rgba(253, 236, 156, 0.1), rgba(255, 184, 144, 0.3));
@message-background: linear-gradient(135deg, rgba(250, 222, 111, 0.02), rgba(250, 49, 49, 0.1));
@message-background2: rgb(249 250 251);
@message-color: rgba(99, 102, 241, 0.76);
@message-color2: #666;

//theme3
@toolbar-background: linear-gradient(135deg, rgba(240, 47, 194, 0.8), rgba(96, 148, 234, 0.8));
@toolbox-background: linear-gradient(135deg, rgba(240, 47, 194, 0.4), rgba(96, 148, 234, 0.4));
@top-background: #ffffff44;
@bottom-background: linear-gradient(135deg, #ffe98500, #fa742b00);
@active-background: linear-gradient(135deg, rgba(240, 47, 194, 0.4), rgba(96, 148, 234, 0.4));
@container-background: linear-gradient(180deg, rgba(240, 47, 194, 0.03), rgba(142, 87, 234, 0.1));
@message-background: linear-gradient(135deg, rgba(226, 103, 253, 0.05), rgba(177, 44, 255, 0.2));
@message-background2: rgb(249 250 251);
@message-color: rgba(99, 102, 241, 0.76);
@message-color2: #666;

//theme4
@toolbar-background: linear-gradient(135deg, rgba(255, 247, 32, 0.82), rgba(60, 213, 0, 0.8));
@toolbox-background: linear-gradient(135deg, rgba(255, 247, 32, 0.4), rgba(60, 213, 0, 0.4));
@top-background: #ffffff44;
@bottom-background: linear-gradient(135deg, #ffe98500, #fa742b00);
@active-background: linear-gradient(135deg, rgba(255, 247, 32, 0.6), rgba(60, 213, 0, 0.4));
@container-background: linear-gradient(180deg, rgba(255, 247, 32, 0.02), rgba(60, 213, 0, 0.12));
@message-background: linear-gradient(135deg,#fff720,#3cd500);
@message-background2: linear-gradient(135deg, rgba(255, 247, 32, 0.25), rgba(60, 213, 0, 0.25));
@message-color: rgba(99, 102, 241, 0.76);
@message-color2: #666;

//theme5
@toolbar-background: linear-gradient(135deg, rgba(23, 234, 217, 0.82),  rgba(96, 120, 234, 0.8));
@toolbox-background: linear-gradient(135deg, rgba(23, 234, 217, 0.2),  rgba(96, 120, 234, 0.2));
@top-background: #ffffff44;
@bottom-background: linear-gradient(135deg, #ffe98500, #fa742b00);
@active-background: linear-gradient(135deg, rgba(23, 234, 217, 0.4),  rgba(96, 120, 234, 0.4));
@container-background: linear-gradient(180deg, rgba(23, 234, 217, 0.02),  rgba(96, 120, 234, 0.12));
@message-background: linear-gradient(135deg, rgba(18, 232, 216, 0.9),  rgba(96, 120, 234, 0.9));;
@message-background2: linear-gradient(135deg, rgba(23, 234, 217, 0.1),  rgba(96, 120, 234, 0.1));
@message-color: white;
@message-color2: #666;


.toolbar {
  height: 100vh;
  padding: 32px 24px;
  background-image: @toolbar-background;
  display: flex;
  flex-direction: column;

  .logo {
    width: 40px;
    height: 40px;
  }

  .gap {
    flex: 1;
  }

  .avatar {
    width: 32px;
    height: 32px;
    border-radius: 100%;
    box-shadow: 0 0 8px rgba(227, 216, 253, 0.82);
  }
}

.toolbox {
  height: 100vh;
  width: 280px;
  border: 0;
  background-image: @toolbox-background;

  .title {
    padding: 24px 16px;
    font-size: 20px;
  }

  .search {
    padding: 0 16px;

    input {
      width: 100%;
      height: 40px;
      border: 0;
      border-radius: 10px;
      padding: 12px 18px;
      background: rgba(255, 255, 255, 0.81);
      outline: none;

      &:focus-visible {
        box-shadow: 0 0 8px rgba(83, 83, 234, 0.58);
      }
    }
  }

  .conversations {
    padding-top: 16px;

    .conversation {
      padding: 24px 16px;
      display: flex;
      cursor: pointer;

      &.active {
        background-image: @active-background;
      }

      img {
        width: 32px;
        height: 32px;
        border-radius: 100%;
      }

      .name {
        margin-left: 12px;
        font-weight: bold;
        line-height: 32px;
      }
    }
  }
}

.chatcontainer {
  height: 100vh;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  background-image: @container-background;

  .top {
    padding: 12px 16px;
    border-bottom: 1px solid #18181809;
    display: flex;
    background: @top-background;

    img {
      width: 36px;
      height: 36px;
      margin: 8px;
      border-radius: 100%;
    }

    .title {
      margin: 8px;

      .name {
        font-weight: bold;
      }

      .date {
        font-weight: 300;
        font-size: 13px;
        color: #666;
      }
    }
  }

  .middle {
    padding: 16px;
    flex-grow: 1;

    .message {
      display: flex;
      margin-bottom: 16px;

      &.self {
        flex-direction: row-reverse;

        .content {
          text-align: right;
          color: @message-color2;
          background-image: @message-background2;
        }
      }

      img {
        width: 36px;
        height: 36px;
        margin: 8px;
        border-radius: 100%;
      }

      .content {
        padding: 16px;
        max-width: 420px;
        background-color: #f9fafb;
        background-image: @message-background;
        border-radius: 0 10px 10px 10px;
        color: @message-color;
      }

      .date {
        font-size: 12px;
        color: #999;
        margin: 0 8px;
      }

      .gap {
        flex: 1;
      }
    }
  }

  .bottom {
    padding: 32px 16px 16px 16px;
    background-image: @bottom-background;
    display: flex;

    input {
      flex-grow: 1;
      padding: 0 24px;
      line-height: 24px;
      height: 48px;

      background: rgba(255, 255, 255, 0.81);
      outline: none;
      border: 0;
      border-radius: 10px;

      &:focus-visible {
        box-shadow: 0 0 8px rgba(98, 234, 83, 0.58);
      }
    }
  }
}
</style>
