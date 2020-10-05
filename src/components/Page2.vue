<template>
  <div>      
      <div id="sort-control">
        <a @click="sort('title')">Title</a>
        <a @click="sort('name')">Author(s)</a>
        <a @click="sort('day_publish')">Publish Date</a>
        <a @click="sort('price')">Price</a>
      </div>

        <table id="t-2">
          <tr v-for="(user, index) in sortedUsers" :key="index">
            <td>{{user.title}}</td>
            <td>{{user.name}}</td>
            <td>{{user.day_publish}}</td>
            <td>${{user.price}}</td>
          </tr>
      </table>
      <button><router-link to="/page1">Go to Page 1</router-link></button>
      <button><router-link to="/page3">Go to Page 3</router-link></button>
    </div>
</template>

<script>
export default {
  name: 'Page2',
  data(){
    return {
      currentSort: 'title',
      currentSortType: 'asc',
      users: [
          {
            title: "Drupal 7",
            name: "David Mercer",
            day_publish: "September 2010",
            price: 44.99
          },
           {
            title: "Amazon SimpleDB: LITE",
            name: "Prabhakar Chaganti, Rich Helms",
            day_publish: "May 2011",
            price: 9.99
          },
           {
            title: "Object-Oriented JavaScript",
            name: "Stoyan Stefanov",
            day_publish: "July 2008",
            price: 39.99
          },
           {
            title: "jQuery 1.4 Reference Guide",
            name: "Karl Swedberg, Jonathan Chaffer",
            day_publish: "January 2010",
            price: 39.99
          },
           {
            title: "Cocoa and Objective-C Cookbook",
            name: "Jeff Hawkins",
            day_publish: "May 2011",
            price: 39.99
          },
           {
            title: "Python Testing Cookbook",
            name: "Greg L. Turnquist",
            day_publish: "May 2011",
            price: 44.99
          },
           {
            title: "Linux Shell Scripting Cookbook",
            name: "Sarath Lakshman",
            day_publish: "January 2011",
            price: 44.99
          },
           {
            title: "Nginx 1 Web Server Implementation Cookbook",
            name: "Dipankar Sarkar",
            day_publish: "May 2011",
            price: 39.99
          },
           {
            title: "HTML5 Multimedia Development Cookbookcov.jpg",
            name: "Dale Cruse, Lee Jordan",
            day_publish: "May 2011",
            price: 39.99
          },
           {
            title: "Core Data Essentials.jpg",
            name: "B.M. Harwani",
            day_publish: "April 2011",
            price: 44.99
          },
           {
            title: "WordPress 3 Plugin Development Essentials",
            name: "Brian Bondari, Everett Griffiths",
            day_publish: "March 2011",
            price: 39.99
          },
           {
            title: "LaTeX Beginner's Guide",
            name: "Stefan Kottwitz",
            day_publish: "March 2011",
            price: 44.99
          },
           {
            title: "Panda3D 1.7 Game Developer's Cookbook",
            name: "Christoph Lang",
            day_publish: "March 2011",
            price: 44.99
          },
           {
            title: "CakePHP 1.3 Application Development Cookbook",
            name: "Mariano Iglesias",
            day_publish: "March 2011",
            price: 39.99
          },
           {
            title: "Magento 1.4 Themes Design",
            name: "Richard Carter",
            day_publish: "January 2011",
            price: 39.99
          },
           {
            title: "Django JavaScript Integration: AJAX and jQuery",
            name: "Jonathan Hayward",
            day_publish: "January 2011",
            price: 44.99
          },
           {
            title: "Magento 1.4 Development Cookbook",
            name: "Nurul Ferdous",
            day_publish: "December 2010",
            price: 44.99
          }
      ]
    }
  },
    methods: {
       sort(sortName){
           if(sortName === this.currentSort){
               this.currentSortType = this.currentSortType === 'asc' ? 'desc' : 'asc'
           }
           this.currentSort = sortName;
       }
    },
    computed:{
        sortedUsers() {
            var temp_users = JSON.parse(JSON.stringify(this.users));
            return temp_users.sort((a,b) => {
            let modifier = 1;
            if(this.currentSortType === 'desc') modifier = -1;
            if(a[this.currentSort] < b[this.currentSort]) return -1 * modifier;
            if(a[this.currentSort] > b[this.currentSort]) return 1 * modifier;
            return 0;
            });
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
html, body {
  margin: 0;
  padding: 0;
}

body {
  font: 80% Verdana, Helvetica, Arial, sans-serif;
  color: #000;
  background: #fff;
}
#container {
  margin: 10px 2em;
}

h1 {
  font-size: 2.5em;
  margin-bottom: 0;
}

h2 {
  font-size: 1.3em;
  margin-bottom: .5em;
}
h3 {
  font-size: 1.1em;
  margin-bottom: 0;
}

#sort-control{
  text-align: left;
}

code {
  font-size: 1.2em;
}

a {
  color: #06581f;
  margin: 0 20px;
  cursor: pointer;
  text-decoration: underline;
}


/***************************************
   Chapter Styles
***************************************/

h3 {
  margin: 1em 0;
  font-size: 1.2em;
  line-height: 1;
  padding: .25em .5em;
  color: #333;
}
table {
  margin: 1em 0;
}
tbody td img {
  width: 76px;
  height: 93px;
}
th {
  text-align: left;
  white-space: nowrap;
  background-color: #eee;
}
th.sort a {
  text-decoration: none;
  display: block;
  
}
th.sorted-desc a {
  background-position: 0 -47px;
}
th.sorted-asc a {
  background-position: 0 -97px;
}

th.sort a:hover {
  background-color: #ddd;
}

th.sort a:focus {
  color: #222;
}
th, td {
  padding: 3px 6px;
}
button{
  margin: 0 20px;
}
</style>
