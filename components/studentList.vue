<template >
    <div>
        <h2>Student List</h2><br>
        <table>
            <tr>
           <tr >
                        <th v-for="columns in columnsNames" v-bind:key="columns">{{ columns}}</th>
                       </tr>
                       <tr v-for="(item, index) in   arrStudentList " v-bind:key="item">
                       <td>{{ item.StudentName }}</td>
                       <td> {{ item.StudentRollnum }}</td>
                       <td>{{ item.StudentClass }}</td>
                       <td>{{ item.StudentDivsion }}</td>
                       <td><button class="button" v-on:click="edit_value(index)" >Edit</button></td>
                       <td><button class="button" v-on:click="delete_value(index)">Delete</button></td>
                       </tr>
                
        </table>
    </div>
</template>
<script>
export default {
    name:"StudentList",
    props:['arrStudentList'],
    data(){
        return{
            indx:'',
            columnsNames:["Name","Roll number","Class","Divison","Edit","Delete"]
        };
    },
    methods:{
        edit_value(index)           {
            //alert(index)t
            this.indx=index
             this.$emit('edit-index-value',this.indx)
        },
         delete_value(index)           {
            this.indx=index
            this.$emit('delete-index-value',this.indx)
        }
    }
}
</script>
<style scoped>
.button
{
   width:70px;
   padding: 6px;
   background-color: darkslategray;
   color:white;
   border: 1px solid rgb(189, 167, 167);
    
}
table {
  border-collapse: collapse;
  width: 70%;
}

th, td {
  padding: 8px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}
th {
  background-color: #4CAF50;
  color: white;
}
tr:hover {background-color:#f5f5f5;}
</style>