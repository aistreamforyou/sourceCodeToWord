<template>
  <div>
    <input id="files" type="file" @change="chooseFile()" :webkitdirectory="true"/>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      fileList: [],
      fileMap: {},
    }
  },
  methods: {
    //@todo 设置过滤规则（排除以下文件：1、与webpack相关的；2、与node_modules相关的；3、package-lock.json;4、图片文件（后缀为：png，jpg，svg，gif，））
    //@todo 通过相对路径，设置文件名称的标题级别
    //@todo 将目录导出到word文档
    //@todo 将文件内容高亮显示在桌面
    //@todo 将html内容保存到word中，
      //@todo 方案1：将每个文件内容单独保存到一个word文档中，然后再将多个word文档合并
      //@todo 方案2：对于每一个文件，先设置标题，然后添加格式化后的内容；逐个添加后，最后导出一个word文档
    //获取文件内容
    chooseFile() {
      let list = document.getElementById('files').files
      Array.from(list).forEach(item=>{
        //文件名称
        let fileName = item.name
        //相对路径
        let relaPath = item.webkitRelativePath
        let reader = new FileReader()
        reader.readAsText(item, 'utf-8')
        reader.onload = function (e) {
          console.log(`文件名称：${fileName},相对路径：${relaPath}`)
          // console.log(e.target.result)
        }
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
