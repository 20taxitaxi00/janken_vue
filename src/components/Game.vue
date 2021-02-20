<template>
    <div>
        <div v-if="resultMessage">
            <h2>{{ resultMessage }}</h2>
            <button class="subBtn" v-on:click="start">もう一度！</button>
        </div>
        <div class="imgArea">
            <img v-bind:src="srcList[srcNum]">
        </div>
        <ul class="btnWrapper">
            <li>
                <button class="btn janken" v-on:click="onSelectd" value="0">グー</button>
            </li>
            <li>
                <button class="btn janken" v-on:click="onSelectd" value="1">チョキ</button>
            </li>
            <li>
                <button class="btn janken" v-on:click="onSelectd" value="2">パー</button>
            </li>
        </ul>
    </div>
</template>


<script>
export default {
    name: 'game',
    data() {
        return {
          resultMessage: '',
          srcList: [
              require('../assets/janken/gu.png'),
              require('../assets/janken/cyoki.png'),
              require('../assets/janken/pa-.png')
            ],
          srcNum: 0,
          timer: null
        }
    },
    props: {
        'pushScore': {
            type: Function,
            requrred: true
        }
    },
    created() {
        this.start();
    },
    methods: {
        changeSrcNum() {
            this.srcNum++;
            this.srcNum = this.srcNum % 3;
        },
        start() {
            this.reset();
            this.timer = setInterval(() => {
                this.changeSrcNum()
            }, 100);
        },
        reset() {
            this.resultMessage = '';
            this.timer = null;
            this.resetBtnClass();
        },
        resetBtnClass() {
            const btns = document.querySelectorAll(`.btn`);
            for(let btn of btns) {
                btn.removeAttribute('disabled');
                btn.classList.remove('selectedBtn');
            }
        },
        stop() {
            clearInterval(this.timer);
        },
        onSelected(e) {
            const clickedBtn = e.target;
            this.stop();
            this.judgeGame(+clickedBtn.value, this.srcNum);
            this.pushScore({ msg: this.resultMessage });
            this.changeToNoActiveBtn();
            clickedBtn.classList.add('selectedBtn');
        },
        judgeGame(val, _srcNum) {
            switch(_srcNum) {
                case val:
                    this.resultMessage = 'あいこ'
                    break
                case(val + 1) % 3:
                    this.resultMessage = '勝ち！'
                    break
                case(val + 2) % 3:
                    this.resultMessage = '負け…'
                    break
            }
        },
        changeToNoActiveBtn() {
            const btns = document.querySelectorAll(`.btn`);
            for(let btn of btns) {
                btn.setAttribute('disabled', true);
            }
        }
    }
}
</script>


<style scoped>

</style>