## Les différentes recherches


### Charcrede

Salut! Pour permettre à un utilisateur de passer à la ligne dans un textarea sans soumettre le formulaire lorsqu'il appuie sur la touche "Entrée" (Return), vous pouvez utiliser JavaScript pour empêcher l'événement de soumission par défaut. Voici un exemple simple d'HTML et de JavaScript pour accomplir cela :

```html
<!DOCTYPE html>
<html>
<head>
  <title>Textarea sans soumission</title>
</head>
<body>
  <form id="monFormulaire">
    <textarea id="monTextarea" rows="4" cols="50"></textarea>
    <br>
    <input type="submit" value="Envoyer">
  </form>

  <script>
    // Empêcher la soumission du formulaire lorsque la touche "Entrée" est enfoncée dans le textarea
    document.getElementById("monTextarea").addEventListener("keydown", function(e) {
      if (e.key === "Enter" && !e.shiftKey) {
        e.preventDefault(); // Empêcher la soumission
        // Vous pouvez également ajouter un saut de ligne manuellement
        this.value += "\n";
      }
    });
  </script>
</body>
</html>
```

Dans cet exemple, nous utilisons un gestionnaire d'événements JavaScript pour le textarea. Lorsque l'utilisateur appuie sur la touche "Entrée" sans maintenir la touche Shift enfoncée, l'événement de soumission par défaut est empêché, et nous ajoutons un saut de ligne manuellement en ajoutant "\n" à la valeur du textarea.

Ainsi, l'utilisateur peut passer à la ligne dans le textarea en appuyant sur "Entrée" tout en empêchant la soumission accidentelle du formulaire.