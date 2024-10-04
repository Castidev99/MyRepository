<template>
    <div class="main">
        <h1>Base de datos de los profesores</h1>
    <form class="formulario">
        <input class="form-one" v-model="name" type="text" placeholder="Nombre">
        <input class="form-two" v-model="occupation" type="text" placeholder="Ocupacion">
        <input class="form-three" v-model="skill" type="text" placeholder="Habilidades">
    </form>
    <button class="btn-sendForm" @click="handleClick()">Enviar Info</button>
    {{ saveInfo }}
    {{ newInfo }}
    </div>
</template>

<script setup>
    import { ref } from 'vue';
    //Se recibe y se actualiza la info
    const saveInfo = ref([{
        name: '',
        occupation: '',
        skills: ''
    }])

    const newInfo = ref([])

   
    //Actualizar el nombre del profesor
    const name = ref('')

    //Actualizar la ocupacion
    const occupation = ref('')

    //Actualizar las skills
    const skill = ref('')

    
    //Funcion para manejar la accion del boton
    const handleClick = () => {
        saveInfo.value.map(val => {
            val.name = name.value,
            val.occupation = occupation.value,
            val.skills = skill.value
        
       })
       
 }

    //Storage
    const infoStorage = () =>{
        newInfo.value.push(saveInfo)
}
</script>

<style scoped>
    .main{
        display: flex;
        flex-direction: column;
        gap: 10px;
        justify-content: center;
    }
    .formulario{
        display: flex;
        flex-direction: column;
        gap: 10px;
    }
    .btn-sendForm{
        font-family: monospace;
        width: 100px;
        background-color: darkolivegreen;
        color: white;
        border: 1px solid green;
    }
    .btn-sendForm:hover{
        background-color: white;
        color: rgb(1, 27, 1);
        border: 1px solid darkgreen;
    }
    h1{
        font-family: monospace;
        color: darkolivegreen;
    }
    .form-one, .form-two{
        width: 300px;
        background-color: rgb(195, 228, 147);
    }
    .form-one:hover, .form-two:hover{
        background-color: white;
    }
    .form-three{
        width: 300px;
        height: 100px;
        background-color: rgb(195, 228, 147);
    }
    .form-three:hover{
        background-color: white ;
    }

</style>