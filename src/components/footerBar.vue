<template>
    <div class="footer-wrap">
      <div class="search">
        <el-button class="menu" icon="el-icon-menu"></el-button>
        <el-input v-model="searchText" placeholder="请输入内容" class="input-with-select" style="width:350px;">
            <el-button slot="prepend" icon="el-icon-search"></el-button>
        </el-input>
      </div>
      <div class="business-bar" v-if="navListItem.length > 0">
         <el-tabs  v-model="barIndex" closable @tab-remove="removeTab" type="border-card">
            <el-tab-pane v-for="item in navListItem" :key="item.id" :label="item.name"></el-tab-pane>
        </el-tabs>
      </div>
    </div>
</template>
           
<script>
export default{
    data () {
        return {
            searchText: '',
            navList: [],
            navListItem:[],
            barIndex: '',
        }
    },   
    props: ['index','businessName'],
    watch: {
        searchText(val) {
            this.$emit('searchText', val)
        },
        index(val) {
            console.log(val,'vvvvvv');
            
            this.barIndex = this.index;
            
        },
        businessName(val) {
            let list = [];
            this.navListItem.forEach((item,i) => {
                list.push(item.name);
            })
            if (list.indexOf(val) == -1) {
                this.navListItem.push({id: this.navListItem.length, name: val})
            }
            console.log(this.navListItem);
            
        },
    },
    methods: {
        removeTab(e) {
            console.log(e);
            
            // let tabs = this.navListItem;
            // let activeName = this.barIndex;
            // if (activeName === targetName) {
            // tabs.forEach((tab, index) => {
            //     if (tab.name === targetName) {
            //     let nextTab = tabs[index + 1] || tabs[index - 1];
            //     if (nextTab) {
            //         activeName = nextTab.name;
            //     }
            //     }
            // });
            // }
            
            // this.editableTabsValue = activeName;
            // this.editableTabs = tabs.filter(tab => tab.name !== targetName);
        }
    },
}
</script>
<style lang="scss" scoped>
    .footer-wrap {
        width: 100%;
        height: 40px;
        background: rgba(150, 240, 247, 0.2);
        position: fixed;
        left: 0;
        bottom: 0;
        z-index: 9999999999;
        display: flex;
        flex-direction: row;

        .business-bar {
            margin-left: 20px;
        }
    }        
</style>
<style lang="scss">
// footbar------
 .el-button.menu {
     background: none;
     color: black;
     border: 0;
     font-size: 20px;
     padding: 8px 15px;

     &:hover {
         color: #23aaf2;
     }
 }

 .el-input__inner {
     border-radius: 0;
     border: none;
 }

 .el-tabs--border-card>.el-tabs__header {
     background:  rgba(150, 240, 247, 0.2);
     border: none;
 }
 .el-tabs--border-card>.el-tabs__content {
     padding: 0;
 }
</style>