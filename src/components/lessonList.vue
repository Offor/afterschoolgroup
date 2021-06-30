<template>
    <main>
        <div class="col" v-for="lesson in lessons" :key="lesson.id">
            <figure>
                <img v-bind:src="lesson.image" />
            </figure>
            <h2>Topic: {{lesson.subject}}</h2>
            <p>Location: {{lesson.location}}</p>
             <p>Price: ${{lesson.price}}</p>
             <p>space: {{lesson.space}} </p>
             <button @click="addLesson(lesson)">Add to cart</button>
        </div>
    </main>
    
</template>

<script>
export default {
    name: "lessonList",
    data() {
        return {
            lessons: [
                 {
                id: 101,
                subject: "Maths",
                location: "London",
                price: 100,
                spaces: 5,
                image: "maths.jpg"
            },
            {
                id: 102,
                subject: "English",
                location: "Manchester",
                price: 80,
                spaces: 5,
                image: "english.jpg"
                
            },
            {
                id: 103,
                subject: "Physics",
                location: "Dubai",
                price: 90,
                spaces: 5,
                image: "physics.jpg"
            },
            ],
        }
    },
    methods: {
        addLesson(lesson) {
            console.log("Added Lesson ", lesson.subject)
            this.$emit('addLesson', lesson);
        }

    },
    // computed: {
    //     cartItemCount() {
    //         return this.cart.length || '';
    //     }
    // }
}
</script>
