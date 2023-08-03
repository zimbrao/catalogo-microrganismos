<script>
    export let label = "";
</script>

<style>
    .rounded-box {
        border: 1px solid #000;
        border-radius: 10px;
        padding: 5px;
        padding-top: 15px;
        margin: 10px 0;
        width: max-content;
        position: relative;
    }
    .label {
        position: absolute;
        top: -10px;
        left: 10px;
        background-color: white;
        padding: 0 5px;
    }
</style>

<div class="rounded-box">
    <span class="label">{label}</span>
    <slot></slot>
</div>
