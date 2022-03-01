<template>
  <div class="content">
    <a-row type="flex">
      <a-col v-for="item in Items" :key="item.id" :span="6" :order="item.id" class="card-col">
        <a-card hoverable>
          <img
            slot="cover"
            alt="example"
            src="https://gw.alipayobjects.com/zos/rmsportal/JiqGstEfoWAOHiTxclqi.png"
          />
          <template slot="actions" class="ant-card-actions">
            <a-icon key="view" type="eye" />
            <a-icon key="edit" type="edit" />
            <a-icon key="delete" type="delete" />
          </template>
          <a-card-meta :title="item.title" :description="item.description" @click="handleClick">
            <a-avatar
              slot="avatar"
              src="https://zos.alipayobjects.com/rmsportal/ODTLcjxAfvqbxHnVXCYX.png"
            />
          </a-card-meta>
        </a-card>
      </a-col>
    </a-row>
  </div>
</template>

<script>
export default {
    data () {
        return {
            Items : [
                {id: 1, title: 'SSH 1',description: 'This is a description 1' },
                {id: 2, title: 'SSH 2',description: 'This is a description 2' },
                {id: 3, title: 'SSH 3',description: 'This is a description 3' },
                {id: 4, title: 'SSH 4',description: 'This is a description 4' },
                {id: 5, title: 'SSH 5',description: 'This is a description 5' },
            ]
        }
    },
    methods: {
        handleClick () {
            console.log('click');
        }
    }
}
</script>

<style>
.content {
  background: #222831;
  padding: 20px;
  width: 100%;
  margin: auto;
}
/* .card{
    width: 100%;
    margin-left: 15px;
} */
.card-col{
    padding: 15px;
}

</style>
