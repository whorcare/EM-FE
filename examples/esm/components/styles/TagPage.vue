<template>
  <div class="tag-page">
    <div>
      <h3>切换标签</h3>
      <br>
      <emfe-tag-parent addClass="add" className="default">
        <emfe-tag index="0">默认</emfe-tag>
        <emfe-tag index="1" active=true>选中</emfe-tag>
        <emfe-tag index="2" disable="true">禁止</emfe-tag>
      </emfe-tag-parent>
    </div>
    <br>
    <div>
      <h3>复选标签</h3>
      <br>
      <emfe-tag-parent className="checket">
        <emfe-tag index="0">默认</emfe-tag>
        <emfe-tag index="1">选中</emfe-tag>
        <emfe-tag index="2" disable="true">禁止</emfe-tag>
      </emfe-tag-parent>
    </div>
    <br>
    <div>
      <h3>复选标签带icon</h3>
      <br>
      <emfe-tag-parent className="checket">
        <emfe-tag index="0" :active="active" type="fabu">默认</emfe-tag>
        <emfe-tag index="1" type="fabu">选中</emfe-tag>
        <emfe-tag index="2" type="fabu" disable="true"></emfe-icon>禁止</emfe-tag>
      </emfe-tag-parent>
      <div @click="click">不选中 {{ active }}</div>
    </div>
    <br>
    <div>
      <h3>筛选标签</h3>
      <br>
      <emfe-tag-parent className="screen" skin="blue">
        <emfe-tag index="0"  @tag="tag">默认</emfe-tag>
        <emfe-tag index="1"  @tag="tag">选中</emfe-tag>
      </emfe-tag-parent>
      <br>
      <emfe-tag-parent  addClass="add" className="screen" skin="yellow" :data="dataList">
        <emfe-tag v-for="(item, index) in dataList" :key="index" :index="index" active="true" >{{item}}</emfe-tag>
      </emfe-tag-parent>
    </div>
    <br><br>
    <h3>API</h3>
    <table style="width:100%;text-align:center" class="table">
      <thead>
        <tr>
          <th width="25%">属性</th>
          <th width="30%">说明</th>
          <th width="20%">类型</th>
          <th width="25%">默认值</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>className</td>
          <td>选择皮肤</td>
          <td>String</td>
          <td>必填，值为'default','checket','screen'</td>
        </tr>
        <tr>
          <td>addClass</td>
          <td>自定义的 class 名称。</td>
          <td>String</td>
          <td>默认为""</td>
        </tr>
        <tr>
          <td>disabled</td>
          <td>disabled为 ‘true’时input输入框禁用，disabled为‘false’时input输入框可用</td>
          <td>Boolean,String</td>
          <td>false</td>
        </tr>
        <tr>
          <td>active</td>
          <td>active为默认激活状态</td>
          <td>Boolean,String</td>
          <td>fasle</td>
        </tr>
        <tr>
          <td>index</td>
          <td>子组件索引</td>
          <td>String, Number</td>
          <td>必填</td>
        </tr>
        <tr>
          <td>type</td>
          <td>type 是icon图标的类型</td>
          <td>String</td>
          <td>''</td>
        </tr>
        <tr>
          <td>skin</td>
          <td>筛选标签两种皮肤状态。(yellow|blue)</td>
          <td>String</td>
          <td>-</td>
        </tr>
        <tr>
          <td>click</td>
          <td>点击事件</td>
          <td>Function</td>
          <td>function(){}</td>
        </tr>
      </tbody>
    </table>
    <br><br>
    <table style="width:100%;text-align:center" class="table">
      <thead>
        <tr>
          <th width="33%">事件名</th>
          <th width="33%">说明</th>
          <th width="33%">返回值</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>click(tag 依然能用)</td>
          <td>点击事件</td>
          <td>当前tag的索引值和标签激活状态</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
export default {
  name: 'tag-page',
  data() {
    return {
      dataList: ['默认', '选中'],
      active: true,
    };
  },
  methods:{
    tag(index, activeOk) {
      console.log(index, activeOk);
    },
    click() {
      this.active = !this.active;
    },
  },
};
</script>
