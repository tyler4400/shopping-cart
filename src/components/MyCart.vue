<template>
    <div>
        <h1>我的购物车</h1>
        <table>
            <tr>
                <td>勾选</td>
                <td>课程名称</td>
                <td>课程价格</td>
                <td>数量</td>
                <td>价格</td>
            </tr>
            <tr v-for="(item, index) in CartItem" :key="item.id">
                <td>
                    <input type="checkbox" v-model="item.isChecked" />
                </td>
                <td>{{ item.name }}</td>
                <td>{{ item.price }}</td>
                <td>
                    <button @click="minus(index)">-</button>
                    {{ item.number }}
                    <button @click="add(index)">+</button>
                </td>
                <td>{{ item.price * item.number }}</td>
            </tr>
            <tr>
                <td></td>
                <td colspan="2">{{ checkedCourses }}/{{ allCourseList }}</td>
                <td colspan="2">{{ checkedPrice }}</td>
            </tr>
        </table>

        <hr />
    </div>
</template>

<script>
export default {
    name: 'MyCart',
    data() {
        return {
            CartItem: []
        };
    },
    methods: {
        addToCart(course) {
            const isAlreadyInCart = this.CartItem.find(
                item => item.id === course.id
            );
            if (!isAlreadyInCart) {
                this.CartItem.push({
                    ...course,
                    isChecked: false,
                    number: 1
                });
            } else {
                isAlreadyInCart.number ++;
            }
        },
        minus(index) {
            this.CartItem[index].number --;
            if (this.CartItem[index].number <= 0){
                if (window.confirm('确定删除？')){
                    this.CartItem.splice(index,1);
                }
            }
        },
        add(index) {
            this.CartItem[index].number ++;
        }
    },
    computed: {
        checkedCourses() {
            return this.CartItem.filter(item => item.isChecked).length;
        },
        allCourseList() {
            return this.CartItem.length;
        },
        checkedPrice() {
            let num = 0;
            this.CartItem.forEach(item=>{
                if (item.isChecked){
                    num+= item.price * item.number;
                }
            });
            return num;
        }
    }
};
</script>

<style scoped></style>
