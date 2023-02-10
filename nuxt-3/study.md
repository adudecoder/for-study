# Component Pai
```
<script lang="ts" setup>
    const props = defineProps({
        data: {
            type: Object,
            default: {
                id: '',
                name: '',
            }
        }
    })
</script>
```
Esse ``defineProps`` serve para resgatar uma determinada propriedade do response.

```
<script lang="ts" setup>
    import { useForm } from '@inertiajs/vue3';

    const form = userForm(props.data)
</script>
```
O ``useform`` serve para dizer que é um formulário, inserindo ele dentro de uma constante.

```
<template>
    <form @submit.prevent="form.put(`/registers/complements/${form.id}`, form)">
        
    </form>
</template>
```
A div __pai__ de todas as divs tem que ser transformada em form, dentro do form passamos ``@submit.prevent`` para não atualizar a página, dentro dele chamamos ``form`` e o método ``put()`` passando uma __URL__ + __ID__ ``form.put(`/registers/complements/${form.id}`, form)``  e depois novamente o ``form`` para enviar os dados.

```
<template>
    <form @submit.prevent="form.put(`/registers/complements/${form.id}`, form)">
        <Details
            v-model:name="form.name"
        />
    </form>
</template>
```
Dentro __input__ ou do ``component``(_NESSE EXEMPLO_) passamos o ``v-model`` com o ``form.name``

# Component Filho
```
<script lang="ts" setup>
    const props = defineProps(['name'])
</script>
```
Criamos uma lista com ``defineProps(['name'])`` para vincular o __component pai__ ao __component filho__
```
<div class="w-full xl:mt-0 flex-1">
    <input id="product-name" type="text" class="form-control" 
    v-model="props.name" 
    @input="$emit('update:name', $event.target.value">
</div>
```
E depois faz com que toda entrada(__input__) emita(``$emit``) o valor de quem ta emitindo o evento