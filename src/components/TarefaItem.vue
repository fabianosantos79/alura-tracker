<template>
    <BoxItem>
        <div class="columns">
            <div class="column is-7">
                {{ tarefa.descricao || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <CronometroItem :tempoEmSegundos="tarefa.duracaoEmSegundos" />
            </div>
        </div>
    </BoxItem>
</template>

<script lang='ts'>
import { defineComponent, PropType } from 'vue'
import CronometroItem from './CronometroItem.vue'
import ITarefa from '@/interfaces/ITarefa';
import BoxItem from './BoxItem.vue';

export default defineComponent({
    name: 'TarefaItem',
    components: {
        CronometroItem,
        BoxItem
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
})
</script>