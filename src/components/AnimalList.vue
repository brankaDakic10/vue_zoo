<template>
  <div>
   <form @submit.prevent='addAnimal'>
      <label>Sort</label>
      <input v-model='newAnimal.sort' type='text' placeholder='Enter animal sort'>
      <label>Name</label>
      <input v-model='newAnimal.name'type='text' placeholder='Enter animal name'>
      <label>Date Of Birth</label>
      <input v-model='newAnimal.dateOfBirth' type='text' placeholder='Enter animal date of birth'>
      <button type='submit'>Add Animal</button>
  </form>

   <h2>Animals table</h2>
   <table>
  <thead>
    <th>Species</th>
    <th>Name</th> 
    <th>Date Of Birth</th>
    <th>Sector name</th>
    <th>Sector surface</th>
    <th>&nbsp</th>
    <th>&nbsp</th>
  </thead>
  <tbody>
  <tr v-for="(animal, key) in animals" :key="key" >

    <td>{{animal.sort}}</td>
    <td>{{animal.name}}</td>
   <td>{{animal.dateOfBirth ||'nepoznat'}} </td>

    <td>{{animal.sector.name}} </td>
    <td>{{animal.sector.surface}} </td>
   <td><button @click="removeAnimal(animal)"> Remove </button></td>  
    
    <td><button @click="moveAnimal(animal)"> Move to top </button></td>  
    </tr>
    </tbody>
</table>
      
      
  <h2>Sectors table</h2>
  <table>
  <thead>
    <th>Sector name</th>
    <th>&nbsp</th>
  </thead>
  <tbody>
  <tr v-for="(sector, key) in sectors" :key="key" >
  <td>{{sector.name}}</td>
  <td><button @click="showAnimals(sector)">Show list of animals</button></td> 
  </tr>
  </tbody>
  </table>

 

  </div>
</template>



<script>
const sectors=[
    {name:'Water-animals',surface:'Water'},
    {name:'Fawl',surface:'Kages'},
    {name:'Predators',surface:'Kages'}
  ];



export default {
  name: 'AnimalList',
  data(){
    return{
      
      sectors:sectors,
      animals:[
          {sort:'tiger',name:'Bill',dateOfBirth:'1.4.2017.',sector:sectors[2]},
          {sort:'flamingo',name:'Lena',dateOfBirth:'13.10.2017.',sector:sectors[1]},
          {sort:'leon',name:'Sam',dateOfBirth:'',sector:sectors[2]},
          {sort:'monkey',name:'Joe',dateOfBirth:'11.11.2005.',sector:sectors[1]},
          {sort:'elephant',name:'Nill',dateOfBirth:'19.1.2000.',sector:sectors[1]}
        ]
   ,
      newAnimal:{
          sort:'',
          name:'',
          dateOfBirth:''
            
          }
         }
},

  methods:{

    removeAnimal(animal){

      this.animals.splice(this.animals.indexOf(animal),1);
  },
     moveAnimal(animal){

      this.animals.splice(this.animals.indexOf(animal),1);
      this.animals.unshift(animal);
  },
  addAnimal(){
       this.animals.push(this.newAnimal);
       this.newAnimal={}

    },
   showAnimals(sector){
     var list='';
     this.animals.forEach(function(animal) {
      
      if(animal.sector === sector){
          list+= animal.name+' ';
    }
    });
      alert(list);
   }


   
 }

}
</script>

</style>
