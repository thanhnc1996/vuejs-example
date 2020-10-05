<template>
  <div>
    <div class="masonry">
        <br />
        <br />
        <br />
        <ul class="tabs">
        <li v-for="(tab, index) in tabsList" :key="index" :class="currentIndex == index? 'active' : ''">
            <a @click="chooseTab(index)">{{tab.name}}</a>
        </li>

        </ul>
        <div class="tab_container">
            <div v-for="(tabContent, indexOfTabContent) in tabsContent" :key="indexOfTabContent">
                <div class="tab_content" v-if="indexOfTabContent === currentIndexContent">
                    {{tabContent.content}}
                </div>
            </div>
        </div>
    </div>
    <div>
      <button><router-link to="/page2">Back to Page 2</router-link></button>
    </div>
  </div> 
</template>

<script>
export default {
  name: 'Page3',
  data(){
    return {
      tabsList: [
          {
              name: 'Tab 1',
          },
            {
              name: 'Tab 2',
          },
            {
              name: 'Tab 3',
          }
      ],
      tabsContent: [
          {
              content: "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Dignissimos ratione provident fugit consequuntur tempora esse repellendus, pariatur labore quos qui." 
          },
          {
              content: "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ex suscipit, cupiditate voluptatum facere, quis quibusdam, velit impedit nisi veritatis explicabo cumque at. Facere blanditiis quisquam dolorum, itaque consequuntur, sequi distinctio assumenda! Nisi laboriosam fugit, aliquid esse amet itaque consequuntur ratione?"
          },
          {
              content: "Lorem ipsum dolor"
          }
      ],
      currentIndex: 0,
      currentIndexContent: 0
    }
  },
   methods: {
       chooseTab(index){
           this.currentIndex = index;
           this.currentIndexContent = index;
       }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
body {
  background-color: #DBE4AF;
  font: 14px/20px Arial, Tahoma, Verdana, sans-serif;
  width: 100%;
  height: 100%;
  color: #000;
}

* {
  margin: 0;
  padding: 0;
  outline: none;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

.masonry {
  width: 900px;
  margin: 0 auto;
}

.tabs {
  margin: 0;
  padding: 0;
  list-style: none;
  overflow: hidden;
  border-bottom: 1px solid #999;
}

.tabs li {
  float: left;
  border: 1px solid #999;
  border-bottom: none;
  background: #e0e0e0;
  cursor: pointer;
}

.tabs li a {
  display: block;
  padding: 10px 20px;
  font-size: 16px;
  color: #000;
  text-decoration: none;
}

.tabs li a:hover {
  background: #ccc;
}

.tabs li.active,
.tabs li.active a:hover {
  font-weight: bold;
  background: #fff;
}

.tab_container {
  border: 1px solid #999;
  border-top: none;
  background: #fff;
}

.tab_content {
  padding: 20px;
  font-size: 16px;
}
button{
    margin-top: 20px;
}
</style>
