<template>
    <div>
        <h1>Welcome to home{{title2}}!</h1>
        <input type="text" v-model="input1" />
        <button type="button" @click="getData">Get</button>
        <button type="button" @click="setData">Set</button>

        <select class="form-control" v-model="region" @change="changeRegion">
            <option :key="i" :value="d.v" v-for="(d,i) in options">{{d.t}}</option>
            // d는 options에서 한줄 가져온 데이터의 값이고 , t는 options의 t값
        </select>

        <table class="table table-bordered" v-show="tableShow"> 
        // v-if는 조건이 맞지 않으면 아예 렌더링 하지 않는다 
        // v-show는 조건이 맞든 맞지 않던 일단 렌더링은 한다,,
            <tr :key="i" v-for="(d,i) in options">
                <td>{{d.v}}</td>
                <td>{{d.t}}</td>
            </tr>
        </table>
    </div>
</template>

<script>
    export  default{
        data() {
            return {  // 양방향 바인딩을 지원하기 때문에, 화면상의 input칸에 다른 값을 적어도 그 값이 alert창에 출력됨 
                title : "개발자의 품격",
                title2: "Seoul",
                input1: "abcd",
                options: [
                    {v:"S",t:"Seoul"},
                    {v:"J",t:"Jeju"},
                    {v:"B",t:"Busan"},
                ],
                region: "B",
                tableShow: false,
            };
        },
        watch: { // 항상 모니터링 하다가 데이터가 입력될 경우 계속 보는 것 ,, 데이터 실시간 감지
                // 무튼 매우 중요/ 더 알아 볼 필요가 있다.
            input1() {
                console.log(this.input1);
            },
            title() {
            },
        },
        methods: { //  데이터 컨트롤을 쉽게 할 수 있다.
            getData(){
                alert(this.input1)
            },
            setData(){
            this.input1="12345";
            },
            changeRegion() {
            alert(this.region);
            }
        },
        beforeCreate() {
            //console.log("beforeCreate")
        },
        created() {
            //console.log("created")
        },
        beforeMount() {
            //console.log("beforeMount")
        },
        mounted() {
            //console.log("mounted")
        },
        beforeUpdate(){
            //console.log("beforeUpdate")
        },
        updated() {
            //console.log("updated")
        },
        beforeDestroy(){
            //console.log("beforeDestroy")
        },
        destroyed() {
            //console.log("destroyed")
        },
    };
</script>
