<template actionBarHidden="true">
    <Page actionBarHidden="true" class="app">
     <ActionBar class='header' title=""/>
         <GridLayout class="keyboard" columns="*, *, *, *" rows="*, *, *, *, *, *">
            <Label textWrap="true" class="result" v-model="result" row="0" col="0" colSpan="4"/>/>
            <Button  class="btn act" text="C" @tap="del()" row="1" col="0" colSpan="3"/>
            <Button  class="btn act" text="/" @tap="input('/')" row="1" col="3"/>
           
            <Button  class="btn" text="7" @tap="input('7')" row="2" col="0"/>
            <Button  class="btn" text="8" @tap="input('8')" row="2" col="1"/>
            <Button  class="btn" text="9" @tap="input('9')" row="2" col="2"/>
            <Button  class="btn act" text="*" @tap="input('*')" row="2" col="3"/>
            
            <Button  class="btn" text="4" @tap="input('4')" row="3" col="0"/>
            <Button  class="btn" text="5" @tap="input('5')" row="3" col="1"/>
            <Button  class="btn" text="6" @tap="input('6')" row="3" col="2"/>
            <Button  class="btn act" text="-" @tap="input('-')" row="3" col="3"/>
            
            <Button  class="btn" text="1" @tap="input('1')" row="4" col="0"/>
            <Button  class="btn" text="2" @tap="input('2')" row="4" col="1"/>
            <Button  class="btn" text="3" @tap="input('3')" row="4" col="2"/>
            <Button  class="btn act" text="+" @tap="input('+')" row="4" col="3"/>
            
            <Button  class="btn" text="0" @tap="input('0')" row="5" col="0" colSpan="2"/>
            <Button  class="btn" text="." @tap="input('.')" row="5" col="2"/>
            <Button  class="btn act" text="=" @tap="calc()" row="5" col="3" />
            
         </GridLayout>
    </Page>
</template>

<script >
    export default  {
    data() {
        return {
            result: '',
      }
    },
    methods:{
            input: function(char){
                this.result = this.result.toString();
                this.result += char;
            },
            calc: function(){
                try{
                    this.result = eval(this.result);
                    if (isNaN(this.result)) {
                        throw new Error();
                  }
                }
                catch{
                    this.result = 'invalid input';
                }
            },
            
            del: function(){
                this.result = '';
            }

           
    } 
  }
</script>

<style scoped>
    .header{
        background-color: #fff;
    }
    .app{
        background-color: #fff;
    }
    .result{
        text-align: right;
        font-size: 28px;
        overflow-wrap: break-word;
        color: #9a001e;
    }
    .btn{
        background-color: #ffc040;
        color: #9a001e;
        border: solid;
        border-width: 2px;
        border-color: rgba(9, 10, 9, 0.616);
        width: 420px;
        height: 420px;
    }
    .btn[text="C"]{
        width: 1260px;
    }
    .btn[text='0']{
        width: 840px;
    }
    .btn:active {
         background-color: #34d0ba;
    }
    .act {
        background-color: #34d0ba;
    }
    .act:active {
        background-color: rgb(17, 16, 16);
    }
</style>