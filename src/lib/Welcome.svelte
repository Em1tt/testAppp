<script lang="ts">
  let rule1, rule2: boolean;
  let disabled: boolean =true;
  let classOne, classTwo: string = "";
  classTwo = "disappeared";
  import { v4 as uuidv4 } from 'uuid';
  async function showRegister(){
    classOne="disappear";
    classTwo="appear";
  }
  $: if(rule1 && rule2){
    disabled=false;
  }else{
    disabled=true;
  }
  let name, password, confirmPassword: string;
  async function register(form){
    console.log(form);
    const body = {
      name,
      password,
      confirmPassword
    };
  }
  function fetchTurnstile(data){
    console.log(data);
  }
</script>

<div class="welcome">
  <div>
    <h1>SSOSTA.chat</h1>
    <form class="{classOne}" on:submit|preventDefault={showRegister}>
      <fieldset>
        <input bind:checked={rule1} type="checkbox" name="rule1" id="rule1" />
        <label for="rule1" />
        <label for="rule1"
          >Sľubujem, že budem udržiavať <b>len civilné diskúsie</b>, bez rasizmu
          alebo iných extremistických ideológií.</label
        >
      </fieldset>
      <fieldset>
        <input bind:checked={rule2} type="checkbox" name="rule1" id="rule2" />
        <label for="rule2" />
        <label for="rule2"
          >Beriem na vedomie, že moje správy vidia všetci, kedykoľvek.</label
        >
      </fieldset>
        <button {disabled} type="submit">Poďme na to!</button>
    </form>
    <form class="{classTwo} register" on:submit|preventDefault={register}>
      <fieldset>
        <input bind:value={name} type="text" placeholder="Login"/>
      </fieldset>
      <fieldset>
        <input bind:value={password} type="password" placeholder="Heslo"/>
      </fieldset>
      <fieldset>
        <input bind:value={confirmPassword} type="password" placeholder="Potvrď Heslo"/>
      </fieldset>
      <div class="cf-turnstile" data-sitekey="{import.meta.env.PUBLIC}" data-callback="{fetchTurnstile}"></div>
        <button {disabled} type="submit">Poďme na to!</button>
    </form>
  </div>
</div>
