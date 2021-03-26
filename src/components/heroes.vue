<template>
  <div class="content-container">
    <div class="section content-title-group">
      <h2 class="title">Heroes</h2>
    </div>
    <div class="columns">
      <div class="column is-3">
        <div class="card" v-show="heroes.length">
               <header class="card-header">

          <p class="card-header-title">heroes list</p>
        </header>
        <ul class="list is-hoverable">
          <li v-for="hero in heroes" :key="hero.id">
            <a
              class="list-item"
              @click="selectedHero = hero"
              :class="{ 'is-active': selectedHero === hero }"
              ><span>{{ hero.firstName }}</span></a
            >
          </li>
        </ul>
        
        </div>
     
      </div>
    </div>
        <div class="columns" v-if="selectedHero">
            <div class="column is-8">
                <div class="card edit-detail">
                    <header class="card-header">
                        <p class="card-header-title">{{ fullName}}</p> 
                    </header>
                    <div class="card-content">
                        <div class="content">
                            <div class="field">
                                <label class="label" for="id">id</label>
                                <label class="input" id="id" readonly>{{selectedHero.id}}</label>
                            </div>
                            <div class="field">
                                <label class="label" for="firstName">Primer Nombre</label>
                                <input class="input" id="firstName" v-model="selectedHero.firstName" />                                
                            </div>
                             <div class="field">
                                <label class="label" for="lastName">Segundo Nombre</label>
                                <input class="input" id="lastName" v-model="selectedHero.lastName" />                                
                            </div>
                            <div class="field">
                                <label class="label" for="description">Descripcion</label>
                                <textarea
                                    class="input"
                                    id="description"
                                    type="text"
                                    v-model="selectedHero.description"
                                />
                            </div>
                            <div class="field">
                                <label class="label">Color de la capa</label>
                                <label class="radio" for="color-red">
                                    <input 
                                        type="radio"
                                        id="color-red"
                                        value="red"
                                        v-model="selectedHero.capeColor"
                                    />
                                    Rojo
                                </label>
                                <label class="radio" for="color-blue">
                                    <input 
                                        type="radio"
                                        id="color-blue"
                                        value="blue"
                                        v-model="selectedHero.capeColor"
                                    />
                                    Azul
                                </label>
                                 <label class="radio" for="color-green">
                                    <input 
                                        type="radio"
                                        id="color-green"
                                        value="green"
                                        v-model="selectedHero.capeColor"
                                    />
                                    Verde
                                </label>
                                <div
                                    class="color-line"
                                    :style="{'background-color': selectedHero.capeColor}"
                                    >
                                </div>
                            </div>
                            <div class="field">
                                <label for="power">
                                    Super Poderes
                                    <div class="select is-primary">
                                        <select 
                                            id="power"
                                            v-model="selectedHero.power"
                                            :class="{invalid: !selectedHero.power}"
                                           
                                        >
                                            <option disabled value>Por favor seleccione uno</option>
                                            <option>Velocidad</option>
                                            <option>Volar</option>
                                            <option>Fuerza</option>
                                            <option>Invisibilidad</option>
                                        </select>
                                    </div>
                                </label>
                            </div>
                            <div class="field">
                                <label class="checkbox" for="active">
                                    active
                                    <input
                                        type="checkbox"
                                        class="is-primary"
                                        id="active"
                                        v-model="selectedHero.active"
                                    />
                                </label>
                            </div>
                        </div>
                    </div>
                     <footer class="card-footer">
                        <button
                        class="link card-footer-item cancel-button"
                        @click="cancelHero()"
                        >
                        <i class="fas fa-undo"></i>
                        <span>Cancel</span>
                    </button>
            <button class="link card-footer-item" @click="saveHero()">
              <i class="fas fa-save"></i>
              <span>Save</span>
            </button>
          </footer>
        </div>
        <div class="notification is-info" style="background:blue;">
          <pre>{{ message }}</pre>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    name:'Heroes',
    data(){
        return {
            selectedHero:undefined,
            heroes:[
                {
                    id: 10,
                    firstName: 'Ella',
                    lastName: 'Papa XX',
                    description: 'fashionista',
                    capeColor: 'green',
                    power: 'Fuerza',
                    active: true,
                },
                {
                    id: 20,
                    firstName: 'Madelyn',
                    lastName: 'Papa Y',
                    description: 'the cat whisperer',
                    capeColor: 'blue',
                    power: 'Velocidad',
                    active: true,

                },
                {
                    id: 30,
                    firstName: 'Haley',
                    lastName: 'Papa G',
                    description: 'pen wielder',
                    capeColor: 'red',
                    power: 'Invisibilidad',
                    active: true,
                },
                {
                    id: 40,
                    firstName: 'Landon',
                    lastName: 'Papa R',
                    description: 'arc trooper',
                    capeColor: 'red',
                    power: 'Invisibilidad',
                    active: true,
                },
            ],
            message:''
        };
    },
    computed: {
        fullName() {
            return `${this.selectedHero.firstName} ${this.selectedHero.lastName}`;
        }
    },
    methods:{
        
    },

}
</script>

