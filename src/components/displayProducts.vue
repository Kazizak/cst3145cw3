<template>
    <div>
      <div v-for="course in courses"  :key="course.id">
        <div id="course_templates">
         <img style="width: 100px; height:100px;" v-bind:src="course.image">
          <h2>Subject : {{course.subject}}</h2>
          <p>Campus : {{course.campus}}</p>
          <p>Price : {{course.price}}</p>
          <p>Available Spaces : {{course.spaces}}</p>
          <input type="button" value="Add To Cart" :disabled="course.A_D" @click="addtocart(course._id)">
        </div>
      </div>
    </div>
</template>

<script>
export default{
    name: "displayProducts",
    props:['courses'],
    data(){
        return{ coursesL : this.courses}
    },
    computed :{
        filtered_courses() {
            return this.courses.filter((course) => {
            return course.subject.match(this.search_term) || course.campus.match(this.search_term);
            })
        }
    },
    methods: {
        addtocart(id){
            this.$emit('addproduct',id);
        }
    }
}
</script>

<style>
#course_templates{
    border : 1px solid black;
    float: left;
    padding: 30px;
    margin : 20px;
    border-radius :10px;
    font-size: 20px;
}
</style>