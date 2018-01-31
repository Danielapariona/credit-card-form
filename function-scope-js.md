### Variables globales, que van a inicializar con valor definido por el usuario, en la etapa de creación del contexto de ejecución, estás variables estarán almacenadas en memoria.
```js
var $inputCard = $('#card-number');
var $inputMonth = $('.input-month');
var $inputYear = $('.input-year');
var $buttonNext = $('#next');
var regexOnlyNumbers = /^[0-9]+$/;
var labelErrorOrSuccessMessages = $('label[for="card-number"]');
```

### Función anónima que solo se va a ejecutar cuando el usuario realice el evento "input"

```js
$inputCard.on('input', function() {
  isValidCreditCard($(this).val().trim());
});
````

### function statement, acepta hoisting y puede ser utilizada en cualquier parte del programa debido que está almacenado en memoria.

```js
function activeButton() {
  $buttonNext.attr('disabled', false);
} 
 
function desactiveButton() {  
  $buttonNext.attr('disabled', true);
} 

function longitud(input) {
  if (input.trim().length === 16) {
    return input;
  }
}

function soloNumeros(input) {
  # Variable local
  var regex = /^[0-9]+$/;
  if (regex.test(input)) {
    return input;
  }
}
```

### Función statement

```js
  function isValidCreditCard(numberCard) {
    var creditCardNumber = soloNumeros(longitud(numberCard));
    if (creditCardNumber !== undefined) {
      var arr = [];
      var sumaTotal = 0;
      for (var index = creditCardNumber.length - 1; index >= 0; index--) {
        arr.push(creditCardNumber[index]);
      }
      for (var index = 1; index < arr.length; index = index + 2) {
        arr[index] = arr[index] * 2;
        if (arr[index] >= 10) {
          arr[index] = arr[index] - 9;
        }    
      }
     
      for (var index = 0; index < arr.length; index++) {
        sumaTotal = sumaTotal + parseInt(arr[index]);
      }
     
      if (sumaTotal % 10 === 0) {
        console.log('Es una tarjeta valida');
        activeButton();
      } else {
        console.log('No es un numero valido');
        desactiveButton();
      }
    } else {
      console.log('Verifique el numero de su tarjeta'); 
      desactiveButton();  
    }
  }
});
```
### variables locales, que tiene un valor por defecto definido por el usuario.

```js
var creditCardNumber = soloNumeros(longitud(numberCard));
var arr = [];
var sumaTotal = 0;

```