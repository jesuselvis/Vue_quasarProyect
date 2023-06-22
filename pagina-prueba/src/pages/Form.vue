<template>
    <q-page padding>
        <h4>Agregar Productos</h4>

        <pre>{{producto}} - {{seleccion}} - {{terminos}}</pre>

        <q-form 
            class="row q-col-gutter-md"
            @submit.prevent="procesarFormulario"
            @reset="reset"
        
        > 

            <div class="col-12 col-sm-6">
                <q-input
                    label="Producto"
                    v-model="producto"
                    :rules="[ val => val && val.length > 0 || 'No ingresaste nada.']"
                />
            </div>

            <div class="col-12 col-sm-6">
                <q-select 
                    label="Prioridad"
                    v-model="seleccion"
                    :options="opciones"
                    :rules="[ val => val && val.length > 0 || 'No ingresaste nada.']"
                />
            </div>

            <div class="col-12">
                <q-toggle
                    label="Acepta los terminos"
                    v-model="terminos"
                />
            </div>

            <div class="col-12"> 
                <q-btn 
                    color="primary" 
                    label="Enviar" 
                    icon-right="send"
                    type="submit"
                />
                <q-btn  
                    color="primary" 
                    label="Reset"  
                    outline 
                    class="q-ml-sm"
                    :ripple="false"
                    type="reset"
                />
            </div>
        </q-form>
            
    </q-page>
</template>

<script>
import {ref} from 'vue'
import { useQuasar } from 'quasar'
export default{
    setup(){
        const $q = useQuasar()
        const producto = ref(null)
        const seleccion = ref(null)
        const opciones = ['maxima','moderada','minima']

        const procesarFormulario = () => {
            console.log("Me diste click al formulario")
            if (terminos.value === false){
                $q.notify({
                    color: 'red-5',
                    textColor: 'white',
                    icon: 'warning',
                    message: 'Tu no aceptastes los terminos'
                })
            }
            else {
                $q.notify({
                    color: 'green-4',
                    textColor: 'white',
                    icon: 'cloud_done',
                    message: 'Submitted'
                })
            }
        }

        const terminos = ref(false)

        const reset = () => {
            producto.value = null
            seleccion.value = null
            terminos.value = false
        }

        return{
            producto,
            seleccion,
            opciones,
            procesarFormulario,
            terminos,
            reset
        }
    },
}
</script>