<template>
    <div class="h-screen bg-green-400 flex justify-center py-16">
        <div class="w-1/3">
            <div class="p-4 text-right shadow-2x1 rounded-t-lg bg-white">
                <p class="font-semibold text-gray-700 h-6">{{ getOperation }}</p>
                <p class="font-bold text-3x1 text-gray-900 my-2">{{ getResult }}</p>
            </div>

            <div class="grid grid-cols-4 grid-rows-5 shadow-2x1 rounded-b-lg shadow-md">
                <button class="h-16 text-x1 text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="clickLimpar()">Limpar</button>
                <button class="h-16 text-x1 text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="clickDeletar()">Deletar</button>
                <button class="h-16 text-x1 text-white font-semibold bg-gray-800 border-gray-600 hover:bg-gray-700" @click="click('√')">√</button>
                <button class="h-16 text-x1 text-white font-semibold bg-gray-800 border-gray-600 hover:bg-gray-700" @click="clickPorcento()">%</button>

                <button class="h-16 text-x1 text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="click('7')">7</button>
                <button class="h-16 text-x1 text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="click('8')">8</button>
                <button class="h-16 text-x1 text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="click('9')">9</button>
                <button class="h-16 text-x1 text-white font-semibold bg-gray-700 border-gray-600 hover:bg-gray-800" @click="dividir">÷</button>

                <button class="h-16 text-x1 text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="click('4')">4</button>
                <button class="h-16 text-x1 text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="click('5')">5</button>
                <button class="h-16 text-x1 text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="click('6')">6</button>
                <button class="h-16 text-x1 text-white font-semibold bg-gray-700 border-gray-600 hover:bg-gray-800" @click="multiplicar">×</button>

                <button class="h-16 text-x1 text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="click('1')">1</button>
                <button class="h-16 text-x1 text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="click('2')">2</button>
                <button class="h-16 text-x1 text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="click('3')">3</button>
                <button class="h-16 text-x1 text-white font-semibold bg-gray-700 border-gray-600 hover:bg-gray-800" @click="subtrair">−</button>

                <button class="h-16 text-x1 text-white font-semibold bg-green-500 border-green-400 col-span-2 hover:bg-green-600" @click="click('0')">0</button>
                <button class="h-16 text-x1 text-white font-semibold bg-green-500 border-green-400 hover:bg-green-600" @click="click('.')">.</button>
                <button class="h-16 text-x1 text-white font-semibold bg-gray-700 border-gray-600 hover:bg-gray-800" @click="somar">+</button>

                <button class="h-16 text-x1 text-white font-semibold bg-green-500 border-green-400 col-span-4 hover:bg-green-600 rounded-b-lg" @click="igual">=</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
   data() {
       return {
           getOperation: '',
           getResult: '0',
           getOperator: null,
           prev: '',
           clic: false,

       }
   },

   methods: {
       clickLimpar() {
           this.getResult = '0';
           this.getOperation = '';
       },
       clickDeletar() {
           if (this.getResult.length > 1){
               this.getResult = this.getResult.substring(0, this.getResult.length - 1);
           } else {
               this.getResult = '0';
           }
       },
       click(par) {
           if (this.getResult == '0'){
               this.getResult = par;
           } else {
               this.getResult += par;
           }
       },
       igual() {
           let operation = this.getResult;
           this.getOperation = operation;
       },
       clickPorcento() {
           this.getResult = this.getResult/100;
       },

       setPrevious() {
           this.prev = this.getResult;
           this.clic = true;
       },
       dividir() {
           this.getOperator = (a, b) => a / b;
           this.setPrevious();
       },
       multiplicar() {
           this.getOperator = (a, b) => a * b;
           this.setPrevious();
       },
       subtrair() {
           this.getOperator = (a, b) => a - b;
           this.setPrevious();
       },
       somar() {
           this.getOperator = (a, b) => a + b;
           this.setPrevious();
       }
   }
}
</script>

<style>
button {
    border: 1px solid;
}
</style>
