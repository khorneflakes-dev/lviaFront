<script>
  
    let nombre = '';
    let apellido = '';
    let instagram_url = '';
    let email = '';
    let telefono = '';
    let direccion = '';
    let ciudad = '';
    let pais = '';
    let departamento = '';
    let edad = '';

    import Imagen1 from '../assets/modelo_frontal.jpg'

    let imagePreview = Imagen1; // Imagen de vista previa por defecto

    function handleFileInput(event) {
      const file = event.target.files[0];
      const reader = new FileReader();

      reader.onload = (event) => {
        imagePreview = event.target.result;
      };

      reader.readAsDataURL(file);
    }

    function handleClick(event) {
      // Hacer clic en la imagen de vista previa enfoca el campo de entrada
      event.preventDefault();
      document.querySelector('input[type="file"]').click();
    }

    async function handleSubmit() {
      const formData = new FormData();
      formData.append('nombre', nombre);
      formData.append('apellido', apellido);
      formData.append('instagram_url', instagram_url);
      formData.append('email', email);
      formData.append('telefono', telefono);
      formData.append('direccion', direccion);
      formData.append('ciudad', ciudad);
      formData.append('pais', pais);
      formData.append('departamento', departamento);
      formData.append('edad', edad);
      formData.append('imagen1', imagePreview)

      const response = await fetch('http://localhost:8000/formulario/', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: formData
        })
      };
  

    
  </script>
<div class="pt-20">

    <input bind:value={nombre} placeholder="nombre" type="text">
    <input bind:value={apellido} placeholder="apellido" type="text">
    <input bind:value={instagram_url} placeholder="https://www.instagram.com/tu_usuario/" type="url">
    <input bind:value={email} placeholder="e-mail" type="email">
    <input bind:value={telefono} placeholder="telefono" type="number">
    <input bind:value={direccion} placeholder="direccion" type="text">
    <input bind:value={ciudad} placeholder="ciudad" type="text">
    <input bind:value={pais} placeholder="pais" type="text">
    <input bind:value={departamento} placeholder="departamento" type="text">
    <input bind:value={edad} placeholder="edad" type="number">

    <!-- <input type="file" on:change={handleFileInputChange} accept="image/*"> -->
    
    <div class="w-44 relative" >
      <label for="fileInput1">
        <img class="w-44 brightness-50" src={imagePreview} alt="" on:click={handleClick}>
      </label>
      <div class="absolute inset-y-1/2 text-center text-[#f6f6f6]" on:click={handleClick}>foto frontal cuerpo completo</div>
      <input id="fileInput1" type="file" on:change={handleFileInput} accept="image/*" hidden />
    </div>

    <button on:click={handleSubmit}>Submit</button>
</div> 