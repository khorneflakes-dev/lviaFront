<script>
  let username = '';
  let password = '';
  let image = null;
  import imagePreview from '../assets/modelo_frontal.jpg'

  const handleSubmit = async () => {
    const formData = new FormData();
    formData.append('username', username);
    formData.append('password', password);
    
    const response = await fetch('http://localhost:8000/login', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({ username, password, image}),
    });
    if (response.ok) {
      alert('Datos enviados correctamente');
    } else {
      alert('Error al enviar los datos');
    }
    
    

  };

  const handleClick = async () => {
    console.log('demo')
  }
</script>

<form on:submit|preventDefault={handleSubmit} class="pt-20">
  <label>
    username
    <input type="text" bind:value={username} />
  </label>
  <label>
    password
    <input type="text" bind:value={password} />
  </label>
  <input type="file" name="" id="" bind:value={image}>
  <!-- <img src={imagePreview} alt='' on:click={handleClick}> -->
  <button type="submit">Enviar</button>
</form>
