<template>
    <div>
        <div>
            <h1>学习商场</h1>
            <hr />
        </div>
        <add-course @addCourse="addCourseToList"></add-course>
        <course-list
            ref="MyCourseList"
            @addCourseToCart="addCourseToCart"
        ></course-list>
        <my-cart ref="MyCart"></my-cart>
    </div>
</template>

<script>
import AddCourse from '@/components/AddCourse';
import CourseList from '@/components/CourseList';
import MyCart from '@/components/MyCart';
export default {
    name: 'StudySquare',
    components: {
        AddCourse,
        CourseList,
        MyCart
    },
    methods: {
        addCourseToList(course) {
            let abc = this.$refs.MyCourseList.addCourse(course);
            abc.then(value => console.log(value));
        },
        addCourseToCart(course) {
            this.$refs.MyCart.addToCart(course);
        }
    }
};
</script>

<style scoped></style>
