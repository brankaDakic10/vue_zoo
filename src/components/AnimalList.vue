<template>
  <div>
   <table>
  <thead>
    <th>Sort</th>
    <th>Name</th> 
    <th>Date Of Birth</th>
     <th>&nbsp</th>
     <th>&nbsp</th>
  </thead>
  <tbody>
  <tr v-for="(animal, key) in animals" :key="key" >

    <td>{{animal.sort}}</td>
    <td>{{animal.name}}</td>
   <td>{{animal.dateOfBirth ||'nepoznat'}} </td>
    <td> 
    <button @click="removeAnimal(animal)"> Remove </button> 
    </td> 
    <td> 
    <button @click="moveAnimal(animal)"> Move to top </button> 
    </td> 
    </tr>
   </tbody>
</table>
   
  </div>
</template>



<script>
export default {
  name: 'AnimalList',
  data(){
    return{

 animals:[
     {sort:'tiger',name:'Bill',dateOfBirth:'1.4.2017.'},
     {sort:'flamingo',name:'Lena',dateOfBirth:'13.10.2017.'},
     {sort:'leon',name:'Sam',dateOfBirth:''},
     {sort:'monkey',name:'Joe',dateOfBirth:'11.11.2005.'},
     {sort:'elephant',name:'Nill',dateOfBirth:'19.1.2000.'}
   ]


  }
},

  methods:{

    removeAnimal(animal){

      this.animals.splice(this.animals.indexOf(animal),1);
  },
     moveAnimal(animal){
       
      this.animals.splice(this.animals.indexOf(animal),1);
      this.animals.unshift(animal);
    
      
     }
   


   
 }

}
</script>

</style>
