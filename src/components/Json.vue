<template>
<div>
    <el-row type="flex" class="row-bg" justify="center" :gutter="20">
        <el-col :span="18">
            <el-input
                    type="textarea"
                    :rows="8"
                    placeholder="请输入json内容"
                    resize="none"
                    @change="parseJson"
                    v-model="text.input"
            >
            </el-input>
        </el-col>
    </el-row>
    <el-row type="flex" class="row-bg" justify="center">
        <el-col :span="18">
            <div id="editor"></div>
        </el-col>
    </el-row>
</div>
</template>

<script>
export default {
    name: 'json',
    data () {
        return {
            text: {
                input: ""
            },
            editor: undefined
        }
    },
    mounted () {
        var e = document.getElementById("editor")
        this.editor = new JSONEditor(e, {
            modes: ["code", "text", "tree", "view"],
        })
    },
    methods: {
        parseJson (val) {
            try {
                this.editor.set(JSON.parse(val))
            } catch(e) {}
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.row-bg {
    margin-bottom: 20px;
}

</style>
