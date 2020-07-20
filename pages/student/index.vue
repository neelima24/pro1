<template >
    <div >
        <div>
        <p>{{ error }}</p>
        <table>
            <tr>
                <td>
                    <label class="label form">Student Name</label><br>
                    <input type="text form"  class="inputext form" v-model="student.studentName" placeholder="enter student name"/>
       
                </td>
                <td>
                    <label  class="label form">Roll Number </label><br>
                    <input type="text" class="inputext form" v-model="student.studentRollno" placeholder="enter Roll number"/><br>
                </td>
            </tr>
            <tr>
                 <td>
                    <label  class="label form" >Class </label><br>
                    <input type="text" class="inputext form" v-model="student.studentClass" placeholder="enter class"/><br>
                 </td>
                 <td>
                     <label  class="label form">Division</label><br>
                     <input type="text" class="inputext form" v-model="student.studentDivision" placeholder="enter division"/><br>
                 </td>
             </tr>
        </table>
        <button type="button"  v-on:click="saveStudent()" class="button form">Save Student</button>
   
    </div>
    <br>
     <studentList v-if="arrStudentList.length" v-bind:arrStudentList="arrStudentList" v-on:edit-index-value="editRow" v-on:delete-index-value="deletetRow"/>
    </div>
</template>
<script>

import studentList from '@/components/studentList.vue';
export default {
  
    components:{
        studentList
    },
    data(){
        return{
            error:'',
            editIndex:-1,
            student:{
                studentName:'',
                studentRollno:'',
                studentClass:'',
                studentDivision:''
            },
            arrStudentList:[]
        };
    },
    methods:{
        saveStudent:function(){
            let arrStudentList={
                                'StudentName':this.student.studentName,
                                'StudentRollnum':this.student.studentRollno,
                                'StudentClass':this.student.studentClass,
                                'StudentDivsion':this.student.studentDivision
                            }
            if(this.editIndex==-1){
             this.arrStudentList.push(arrStudentList);
            }
            else
            {
                this.arrStudentList.splice(this.editIndex,1,arrStudentList);
                this.editIndex=-1;

            }
                             
                             this.student.studentName=''
                             this.student.studentRollno=''
                             this.student.studentClass=''
                             this.student.studentDivision=''

        },
        async editRow(index){
            this.editIndex=index;
            this.student.studentName=this.arrStudentList[index].StudentName;
            this.student.studentRollno=this.arrStudentList[index].StudentRollnum;
            this.student.studentClass=this.arrStudentList[index].StudentClass;
            this.student.studentDivision=this.arrStudentList[index].StudentDivsion;


        },
         async deletetRow(index){
              this.arrStudentList.splice(index,1);
         }

    }
   
}
</script>
<style scoped>

.form{
 padding: 8px;
 margin-left:6px;
 display: inline-block;
 border-radius:3px;
 font-size: 15px;
}
.label {
  color:rgb(48, 13, 13);
  font-family: Arial;
  
  
}
.inputext{
 margin-bottom:8px;
 display: inline-block;
 border-bottom: 1px solid rgb(201, 138, 138);

}
.button
{
    width:200px;
    background-color: rgb(10, 150, 96);
    color:white;
    border: 1px solid rgb(107, 190, 128);
    
}

</style>