<template>
    <div>
        <h2>Checkout</h2>
        <h3>Added Lessons</h3>
        <div v-for="lesson in cart" :key="lesson.id" >
           <figure>
                <img v-bind:src="lesson.image" />
            </figure>
            <h2>Topic: {{lesson.subject}}</h2>
            <p>Location: {{lesson.location}}</p>
             <p>Price: ${{lesson.price}}</p>
             <p>Spaces: {{lesson.spaces}}</p>
             <button @click="deleteLesson(lesson)">Remove</button>
        </div>
        <p>
            <strong>Name: </strong> <input type="text" v-model="name" />
            <strong>Phone: </strong> <input type="number" v-model="phone" />
            <button :disabled='isDisabled' @click="saveOrder">Submit</button>
        </p>
    </div>
</template>

<script>
export default {
   name: "Checkout",
   props: ['cart'],
   data() {
       return {
           name:"",
           phone:"",
           
       }
   },
   methods: {
       deleteLesson(lesson) {
           console.log("Deleted Lesson", lesson.subject)
           this.$emit('deleteLesson', lesson);
       },

       saveOrder() {
           alert("Order Succefully")
       }
   },

   computed: {
       isDisabled() {
           return !this.name || !this.phone;
       }
   }
}
</script>
