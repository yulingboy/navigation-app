<template>
    <div class="header-box">
        <div class="header-left">晨风</div>
        <div class="header-right">
            <ul>
                <li>更多站点</li>
                <li>自定义模式</li>
                <li>快捷键</li>
                <li>关于</li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {}
</script>

<style scoped lang="scss">
.header-box {
    height: 100px;
    width: 80%;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    // background-color: #fff;
    .header-left {

    }
    .header-right {
        li {
            float: left;
            margin: 0 10px;
            color: #fff;
            cursor: pointer;
        }
    }
}
</style>