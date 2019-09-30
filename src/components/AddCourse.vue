<template>
    <div>
        <h1>添加课程(后台)</h1>
        <div>
            <label>
                课程名称: <input type="text" v-model="course.name" />
            </label>
        </div>
        <div>
            <label>
                课程价格: <input type="number" v-model="course.price" />
            </label>
        </div>
        <div>
            <button @click="addCourseToList">添加课程到列表</button>
        </div>
        <hr />
    </div>
</template>

<script>
export default {
    name: 'AddCourse',
    data() {
        return {
            course: {
                name: '',
                price: ''
            }
        };
    },
    methods: {
        addCourseToList() {
            this.$emit('addCourse', {
                ...this.course,
                id: Math.random()
            });
        }
    }
};
</script>

<style scoped></style>
