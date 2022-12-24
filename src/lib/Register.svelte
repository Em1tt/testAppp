<script lang="ts">
    export let start: () => void = ()=>{
        console.log("hi");
    };
    module.exports={
        start: ()=>{
            console.log("hi");
        }
    }
</script>