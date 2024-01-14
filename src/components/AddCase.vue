<template>
    <table>
        <tr>
            <td>
                <input v-model="newName">
            </td>
            <td>
                <button @click="$emit('add', newName)">Сохранить</button>
            </td>
        </tr>
    </table>
</template>

<script>
    export default {
        emits: ['add'],
        data() {
            return {
                newName: ''
            }
        },
    }
</script>