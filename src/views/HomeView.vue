<template>
    <el-container class="h-lvh">
        <el-menu default-active="2" class="el-menu-vertical-demo relative" :collapse="isCollapse" @open="handleOpen"
            @close="handleClose">
            <el-image src="https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png"
                class="w-full h-[50px]" fit="fill" />
            <el-button-group class="absolute top-2 right-[-25px]">
                <el-button @click="isCollapse = !isCollapse" type="primary" v-if="!isCollapse">
                    <el-icon>
                        <ArrowRightBold />
                    </el-icon></el-button>
                <el-button @click="isCollapse = !isCollapse" type="primary" v-if="isCollapse"><el-icon>
                        <ArrowLeftBold />
                    </el-icon></el-button>
            </el-button-group>
            <el-sub-menu index="1">
                <template #title>
                    <el-icon>
                        <location />
                    </el-icon>
                    <span>Navigator One</span>
                </template>
                <el-menu-item-group>

                    <template #title><span>Group One</span></template>
                    <el-menu-item index="1-1">item one</el-menu-item>
                    <el-menu-item index="1-2">item two</el-menu-item>
                </el-menu-item-group>
                <el-menu-item-group title="Group Two">
                    <el-menu-item index="1-3">item three</el-menu-item>
                </el-menu-item-group>
                <el-sub-menu index="1-4">

                    <template #title><span>item four</span></template>
                    <el-menu-item index="1-4-1">item one</el-menu-item>
                </el-sub-menu>
            </el-sub-menu>
            <el-menu-item index="2">
                <el-icon><icon-menu /></el-icon>

                <template #title>Navigator Two</template>

            </el-menu-item>
            <el-menu-item index="3">
                <el-icon>
                    <setting />
                </el-icon>

                <template #title>Navigator Four</template>
            </el-menu-item>
        </el-menu>
        <el-container>
            <el-header style="text-align: right; font-size: 18px">
                <div class="toolbar">
                    <el-dropdown>
                        <el-icon style="margin-right: 8px;font-size: 20px;">
                            <setting />
                        </el-icon>

                        <template #dropdown>
                            <el-dropdown-menu>
                                <el-dropdown-item>View</el-dropdown-item>
                                <el-dropdown-item>Add</el-dropdown-item>
                                <el-dropdown-item>Delete</el-dropdown-item>
                            </el-dropdown-menu>
                        </template>
                    </el-dropdown>
                    <span>Tom</span>
                </div>
            </el-header>

            <el-main class="bg-slate-800">
                <DialogView />
                <el-scrollbar>
                    <el-table :data="tableData">
                        <el-table-column prop="date" label="Date" width="140" />
                        <el-table-column prop="name" label="Name" width="120" />
                        <el-table-column prop="address" label="Address" />
                    </el-table>
                </el-scrollbar>
            </el-main>
        </el-container>
    </el-container>
</template>

<script lang="ts" setup>
import { ref } from "vue";
import DialogView from "../components/DialogView.vue";
import { Menu as IconMenu, Location, Setting } from "@element-plus/icons-vue";
const isCollapse = ref(true);
const handleOpen = (key: string, keyPath: string[]) => {
    console.log(key, keyPath);
};
const handleClose = (key: string, keyPath: string[]) => {
    console.log(key, keyPath);
};
const item = {
    date: "2016-05-02",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
};
const tableData = ref(Array.from({ length: 20 }).fill(item));
</script>

<style scoped>
.layout-container-demo .el-header {
    position: relative;
    background-color: var(--el-color-primary-light-7);
    color: var(--el-text-color-primary);
}

.layout-container-demo .el-aside {
    color: var(--el-text-color-primary);
    background: var(--el-color-primary-light-8);
}

.layout-container-demo .el-menu {
    border-right: none;
}

.layout-container-demo .el-main {
    padding: 0;
}

.layout-container-demo .toolbar {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    height: 100%;
    right: 20px;
}

.el-menu-vertical-demo:not(.el-menu--collapse) {
    width: 200px;
    min-height: 400px;
}
</style>