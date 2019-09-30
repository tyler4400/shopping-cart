<template>
    <div>
        <h1>课程列表</h1>
        <table>
            <tr>
                <th>课程名称</th>
                <th>课程价格</th>
                <th>操作</th>
            </tr>
            <tr v-for="(course, index) in courseList" :key="index">
                <td>{{ course.name }}</td>
                <td>{{ course.price }}</td>
                <td>
                    <button @click="addCourseToCart(course.id)">
                        添加到购物车
                    </button>
                </td>
            </tr>
        </table>

        <hr />
    </div>
</template>

<script>
export default {
    name: 'CourseList',
    data() {
        return {
            courseList: [
                {
                    id: 0,
                    name: 'web全栈开发架构师',
                    price: 9998
                },
                {
                    id: 1,
                    name: 'Python人工智能',
                    price: 8888
                }
            ]
        };
    },
    methods: {
        addCourse(course) {
            if (!course) {
                return;
            }
            this.courseList.push(course);
            return new Promise(resolve => {
                resolve('返回一个promise对象，有时addCourse会失败，这里便可以扩展');
            });
        },
        // 这个方法用下标index更好一些
        addCourseToCart(id){
            const course = this.courseList.find(item => item.id === id);
            this.$emit('addCourseToCart', course);
        }
    }
};
</script>

<style scoped></style>
