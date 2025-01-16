<template>
    <!-- в {{  }} указывается, что мы возвращаем из нашего объекта дата в формате ключ знаение, это может быть текст, число, булеан и т.д.-->
    <h1 class="title">Test vue js 3 - {{ title }}</h1>
    <p class="desription">{{ description }}</p>
    <div>{{ num }}</div>

    <!-- теперь давайте создадим обработчик, сделаем кнопку и на нее повесим клик, клик можно записать: @click, onclick, v-on:click, чаще всего пишут просто @click  - после передадим туда действие например текст новый в переменную 
    По мимо клика можно использовать что угодно как и в js, например давайте сделаем что то с мышкой 
    -->
    <button type="button" @click="this.description = 'Отправлено'">Отправить</button>
    <button type="button" @mouseenter="this.description = 'Навелись мышкой'">Отправить</button>

    <!-- такая запись длинная имеет место, но не прям удобна, сделаем похожее, но уже через метод (methods) и передадим его работу-->
    <p class="info">{{ this.text }}</p>
    <button class="info__btn" @click="newText()">{{ this.textBtn }}</button>


    <!-- так же в функциях можно как и в простом js передавать параметры, сделаем еще 1 пример с функцией при клике, увеличим число + передадим информацию -->

    <span class="number">{{ this.number }}</span>
    <span class="number__info">{{ this.numberInfo }}</span>
    <button class="number__btn" @click="numberPlus('число увеличено!')">{{ this.numberBtn }}</button>

    <!-- а теперь тоже самое, только не укажем параметр функции в плане текста, но добавим его В САМОЙ функции просто сделав: text = 'Да, число увеличилось!'  - оно будет просто стандартное, если мы не передадим пареметр, это может быть и текст и число, и данные и т.д.
    -->
    <button class="number__btn" @click="numberPlus()">{{ this.numberBtn }}</button>
</template>

<script>
// в теге скрипт указываем, что вообще будет экспортироваться из тега template
export default {
    data() {
        return {
            description: 'lorem lorem lorem',
            title: 'test VUE 3',
            num: 1234,
            text: 'ffffffffffffffffffffff',
            textBtn: 'Изменить текст выше',
            number: 0,
            numberBtn: 'Нажимай',
            numberInfo: 'число увеличено на: ',
        }
    },

    methods: {
        newText() {
            this.text = 'ddddddddddddddddddddddddd';
            this.textBtn = 'Текст изменен';
        },
        numberPlus(text = 'Да, число увеличилось!') {
            if (this.number < 1) {
                this.number = `${this.number + 1} ${text}`
                this.numberInfo += this.number.slice(0, 1);
                return;
            }
        }
    },
}
</script>

<style scoped>
.title {
    color: black;
    line-height: 100%;
    font-size: 40px;
}

.desription {
    font-size: 30px;
    line-height: 100%;
}

.info {
    color: blue;
    font-size: 30px;
}

.info__btn {
    color: blue;
    font-size: 20px;
    padding: 10px;
}

.number {
    display: block;
    margin-top: 20px;
    font-size: 30px;
}

.number__info {
    display: block;
    margin-bottom: 10px;
}
</style>
