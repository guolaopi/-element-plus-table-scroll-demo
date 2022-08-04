<template>
    <h2>Try to scroll the table.</h2>
    <el-table
        height="200"
        key="id"
        border
        v-scrollLoad="scrollLoad"
        :data="data"
    >
        <el-table-column
            v-for="item in columns"
            :key="item.prop"
            :prop="item.prop"
            :label="item.label"
        />
    </el-table>
</template>

<script setup>
import { vScrollLoad } from "element-plus-table-scroll";
import { ElMessage } from "element-plus";
import { ref } from "vue";

const columns = ref([
    { prop: "id", label: "ID" },
    { prop: "name", label: "Name" },
    { prop: "sex", label: "Sex" },
]);

const data = ref([
    { id: 1, name: "UserA", sex: "Male" },
    { id: 2, name: "UserB", sex: "Female" },
    { id: 3, name: "UserC", sex: "Male" },
    { id: 4, name: "UserD", sex: "Male" },
    { id: 5, name: "UserE", sex: "Female" },
    { id: 6, name: "UserF", sex: "Male" },
    { id: 7, name: "UserG", sex: "Male" },
    { id: 8, name: "UserH", sex: "Female" },
    { id: 9, name: "UserI", sex: "Female" },
]);

function scrollLoad(e) {
    if (
        e.target.offsetHeight + e.target.scrollTop + 50 >=
        e.target.scrollHeight
    ) {
        console.log(1);
        data.value = data.value.concat(data.value);
    }
}
</script> 