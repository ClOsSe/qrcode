<template>
    <div class="col-12 center" align="center">
        <div id="qrcode-container">
            <canvas style="width:150px;height:150px" id="canvas"></canvas>
        </div>
    </div>
</template>
<script lang="ts">
    
import { Component, Prop, Vue } from 'vue-property-decorator';
import QRCode from 'qrcode'

@Component({
    components:{}
})
export default class Qrcode extends Vue{
    @Prop({default:()=>{return '';}}) url:string;
    mounted(){
        if (this.url != '') {
            QRCode.toCanvas(document.getElementById('canvas'), this.url, function (error:any) {
                if (error) console.error(error)
            console.log('success!');
            })
        }
    }
}
</script>
