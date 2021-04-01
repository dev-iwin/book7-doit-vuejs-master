<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" von:keyup.enter="addTodo"> <!--입력되는 값을 v-model 디렉티브로 data 속성의 newTodoItem과 동기화-->
        <span class="addContainer" v-on:click="addTodo">
            <i class="addBtn fas fa-plus" aria-hidden="true"></i>
        </span>
        <!-- <button v-on:click="addTodo">추가</button> <!--methods 속성에 정의된 함수를 버튼이 클릭되면 수행되도록 v-on 디렉티브 설정-->
    </div>
</template>

<script>
export default {
    data() {
        return {
            newTodoItem: ''
        }
    },
    methods: {
        addTodo() {
            if(this.newTodoItem !== "") {
                var value = this.newTodoItem && this.newTodoItem.trim();
                localStorage.setItem(value, value);
                this.clearInput();
            // 로컬 스토리지에 데이터를 추가하는 setItem(키, 값) API
            // 입력받은 텍스트를 키, 값으로 설정하게 됨
            }
        },
        clearInput() {
            this.newTodoItem = '';
        }
    }
}
</script>

<style scoped>
    input:focus {
        outline: none;
    }
    .inputBox {
        background-color: white;
        height: 50px;
        line-height: 50px;
        border-radius: 5px;
    }
    .inputBox input {
        border-style: none;
        font-size: 0.9rem;
    }
    .addContainer {
        float: right;
        background: linear-gradient(to right, #6478fb, #8763fb);
        display: block;
        width: 3rem;
        border-radius: middle;
    }
    .addBtn {
        color: white;
        vertical-align: middle;
    }

</style>