<template>
    <template v-if="!isEdit">
        <tr :class="{deactive: status}">
            <td>{{ id }}</td>
            <td>{{ name }}</td>
            <td>
                <button @click="update(id)">Редактировать</button>
            </td>
            <td>
                <button @click="remove(id)">Удалить</button>
            </td>
        </tr>
    </template>
    <template v-else>
        <tr>
            <td>
                <input v-model="newName">
            </td>
            <td>
                Статус
                <input v-model="newStatus" type="checkbox">
            </td>
            <td>
                <button @click="save(id)">Сохранить</button>
            </td>
        </tr>
    </template>
</template>

<script>
    export default {
        emits: ['change', 'remove'],
        props: {
            id: Number,
            name: String,
            status: Boolean
        },
        data() {
            return {
                newName: this.name,
                newStatus: this.status,
                isEdit: false,
            }
        },
        methods: {
            update() {
                this.isEdit = true
            },
            save(id) {
                this.isEdit = false
                this.$emit('change', id, this.newName, this.newStatus)
            },
            remove(id) {
                this.$emit('remove', id)
            }
        }
    }
</script>

<style>
    .deactive {
        font-style: italic;
        text-decoration: line-through;
    }
</style>