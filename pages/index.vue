<template>
    <div class="website_navigation-container">
        <el-card class="box-card box">
            <div slot="header" class="clearfix">
                <span>常用网站</span>
                <i
                    style="float: right; padding: 3px 0"
                    class="el-icon-s-tools"
                ></i>
            </div>
            <div class="content">
                <div
                    class="item"
                    v-for="(item, index) in list1"
                    :key="index"
                    @click="handleClick(item)"
                >
                    {{ item.title }}
                </div>
            </div>
        </el-card>
        <el-card class="box-card box">
            <div slot="header" class="clearfix">
                <span>卡片名称</span>
                <el-button style="float: right; padding: 3px 0" type="text"
                    >操作按钮</el-button
                >
            </div>
            <div v-for="o in 4" :key="o" class="text item">
                {{ '列表内容 ' + o }}
            </div>
        </el-card>
        <el-card class="box-card box">
            <div slot="header" class="clearfix">
                <span>卡片名称</span>
                <el-button style="float: right; padding: 3px 0" type="text"
                    >操作按钮</el-button
                >
            </div>
            <div v-for="o in 4" :key="o" class="text item">
                {{ '列表内容 ' + o }}
            </div>
        </el-card>
        <el-card class="box-card box">
            <div slot="header" class="clearfix">
                <span>卡片名称</span>
                <el-button style="float: right; padding: 3px 0" type="text"
                    >操作按钮</el-button
                >
            </div>
            <div class="content">
                <div
                    class="item"
                    v-for="(item, index) in list1"
                    :key="index"
                    @click="handleClick(item)"
                >
                    {{ item.title }}
                </div>
            </div>
        </el-card>
        <el-card class="box-card box">
            <div slot="header" class="clearfix">
                <span>卡片名称</span>
                <el-button style="float: right; padding: 3px 0" type="text"
                    >操作按钮</el-button
                >
            </div>
            <div v-for="o in 4" :key="o" class="text item">
                {{ '列表内容 ' + o }}
            </div>
        </el-card>
        <el-card class="box-card box">
            <div slot="header" class="clearfix">
                <span>卡片名称</span>
                <el-button style="float: right; padding: 3px 0" type="text"
                    >操作按钮</el-button
                >
            </div>
            <div v-for="o in 4" :key="o" class="text item">
                {{ '列表内容 ' + o }}
            </div>
        </el-card>
    </div>
</template>

<script>
export default {
    data() {
        return {
            list1: [
                {
                    title: '百度',
                    url: 'http://www.baidu.com',
                },
                {
                    title: '百度',
                    url: 'http://www.baidu.com',
                },
                {
                    title: '百度',
                    url: 'http://www.baidu.com',
                },
                {
                    title: '百度',
                    url: 'http://www.baidu.com',
                },
                {
                    title: '百度',
                    url: 'http://www.baidu.com',
                },
                {
                    title: '百度',
                    url: 'http://www.baidu.com',
                },
                {
                    title: '百度',
                    url: 'http://www.baidu.com',
                },
                {
                    title: '百度',
                    url: 'http://www.baidu.com',
                },
                {
                    title: '百度',
                    url: 'http://www.baidu.com',
                },
                {
                    title: '百度',
                    url: 'http://www.baidu.com',
                },
                {
                    title: '百度',
                    url: 'http://www.baidu.com',
                },
            ],
            db:null,
        }
    },
    created() {
        this.getJSON()
        this.initDB()
        this.read()
    },
    methods: {
        handleClick(item) {
            window.open(item.url)
        },
        getJSON() {
            this.$axios.get('/json/basicData.json').then((res) => {
                console.log(res)
            })
        },
        initDB() {
            // 创建数据库
            // 第一个参数为数据库名称，第二个数据库为版本号，返回一个IDBOpenDBRequest对象用于操作数据库。
            // 对于open()的第一个参数数据库名，open()会先去查找本地是否已有这个数据库，如果有则直接将这个数据库返回，如果没有，则先创建这个数据库，再返回。对于第二个参数版本号，则是一个可选参数，如果不传，默认为1，但是如果传入必须是一个整数
            // 获取indexedDB对象
            if (process.client) {
                // const idNode = document.getElementById('idName'); // 其实只要你的mounted中涉及对document一类对象的操作，你可以直接在mounted中套一层if (process.client)判断，其他代码也可以写在这个里面。如果你使用了eslint，你可以再在外面套一层注释，让eslint忽略语法检查
                const indexedDB = window.indexedDB || window.webkitIndexedDB || window.mozIndexedDB
                const request = indexedDB.open('myDatabase', 1)
                request.addEventListener('success', (e) => {
                    // 成功处理
                    this.db = e.target.result;
                    console.log('连接数据库成功')
                })
                request.addEventListener('error', (e) => {
                    console.log('连接数据库失败')
                })
            }
        },
        read() {
            var transaction = this.db.transaction(['imgLists'])
            var objectStore = transaction.objectStore('imgLists')
            // 用户读取数据，参数是主键
            var request = objectStore.get(1)

            request.onerror = function (event) {
                console.log('事务失败')
            }

            request.onsuccess = function (event) {
                if (request.result) {
                    console.log(request.result)
                } else {
                    console.log('未获得数据记录')
                }
            }
        },
    },
}
</script>

<style scoped lang="scss">
.website_navigation-container {
    width: 80%;
    margin: 0 auto;
    // background-color: rgba($color: #ffffff, $alpha: 0.4);
    height: calc(100vh - 120px);
    padding: 20px;
    box-sizing: border-box;
    display: flex;
    flex-wrap: wrap;
    ::v-deep .el-card {
        background-color: rgba(255, 255, 255, 0.7) !important;
        border: none !important;
        .el-card__header {
            padding: 10px 20px !important;
            border-bottom: none;
        }
        .el-card__body {
            padding: 0 20px;
        }
    }
    .box {
        width: 32%;
        height: 45%;
        margin-right: 2%;
        &:nth-child(3n) {
            margin-right: 0;
        }
        margin-bottom: 10px;
        .content {
            display: flex;
            flex-wrap: wrap;
            .item {
                cursor: pointer;
                width: 32%;
                background-color: pink;
                margin-right: 2%;
                height: 40px;
                margin-top: 5px;
                text-align: center;
                line-height: 40px;
                &:nth-child(3n) {
                    margin-right: 0;
                }
            }
        }
    }
}
</style>