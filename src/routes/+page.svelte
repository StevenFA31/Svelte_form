<script>
import Button from "./Button.svelte";
import TextArea from "./TextArea.svelte";
import Input from "./Input.svelte";


const forInput = {
    forName : "firstname",
    forType : "",
    forId : "firstname",
    text : "Votre prénom",
    forPlaceholder : ""
}

const forInput2 = {
    forName : "lastname",
    forType : "",
    forId : "lastname",
    text : "Votre nom",
    forPlaceholder : ""
}

const forInput3 = {
    forName : "email",
    forType : "email",
    forId : "email",
    text : "Votre adresse email",
    forPlaceholder : ""
}

const forTextArea = {
    forName : "message",
    forId : "testComment",
    forCols : 30,
    forRows : 1 ,
    forFor : "email",
    text : "Veuillez entrer votre message :"
}

const btnSuccess = {
    forClass : "btn btn-success",
    text : "Envoyer",
}

const btnWarning = {
    forClass : "btn btn-warning",
    text : "Modifier"
}

const btnDanger = {
    forClass : "btn btn-danger",
    text : "Supprimer",
}



    let items = [];

  function handleSubmit(event) {
    event.preventDefault();

    const formData = new FormData(event.target);
    const newItem = {};

    for (const [key, value] of formData.entries()) {
      newItem[key] = value;
    console.log(newItem)

    }

    items = [...items, newItem];
  }

</script>

   
 
  
 

<form action="submit" on:submit={handleSubmit}>
    <Input {...forInput}/>
    <Input {...forInput2}/>
    <Input {...forInput3}/>

<TextArea {...forTextArea}/>

<Button {...btnSuccess}/>
<Button {...btnWarning}/>
<Button {...btnDanger}/>
</form>
<!-- On peux aussi le faire de cette façon !!!  -->

<!-- <Input forName={"firstname"} forId={"firstname"} text={"Votre prénom"} forFor={"firstname"}/>
<Input forName={"lastname"} forId={"lastname"} text={"Votre nom"} forFor={"lastname"}/>
<Input forName={"email"} forType={"email"} forId={"email"} forPlaceholder={"email@exemple.com"} text={"Votre adresse mail"} forFor={"email"}/> -->

<!-- <TextArea forName={"textarea"} forId={"textComment"} forCols={30} forRows={1} forFor="textarea" text={"Entrez votre message"}/> -->

<!-- <Button forClass={"btn btn-success"} text={"Envoyer"}/>
<Button forClass={"btn btn-warning"} text={"Modifier"}/>
<Button forClass={"btn btn-danger"} text={"Supprimer"}/> -->
<br>
<table class="table" >
    <thead>
      <tr>
        <th scope="col">Prénom</th>
        <th scope="col">Nom</th>
        <th scope="col">Adresse mail</th>
        <th scope="col">Message</th>
      </tr>
    </thead>
    <tbody>
        {#each items as item}
        <tr>
          <td>{item.firstname}</td>
          <td>{item.lastname}</td>
          <td>{item.email}</td>
          <td>{item.message}</td>
        </tr>
      {/each}
     
    </tbody>
  </table>

<style>



</style>