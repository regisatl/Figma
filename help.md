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

 ### En vueJS

 Bien sûr, voici comment vous pouvez réécrire le code en utilisant Vue.js, un framework JavaScript populaire. Assurez-vous d'inclure la bibliothèque Vue.js dans votre projet. Voici le code :

```html
<!DOCTYPE html>
<html>
<head>
  <title>Textarea sans soumission avec Vue.js</title>
</head>
<body>
  <div id="app">
    <form @submit.prevent="submitForm">
      <textarea v-model="text" rows="4" cols="50" @keydown.enter.prevent="addNewLine"></textarea>
      <br>
      <input type="submit" value="Envoyer">
    </form>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14"></script>
  <script>
    new Vue({
      el: '#app',
      data: {
        text: '',
      },
      methods: {
        addNewLine() {
          this.text += '\n';
        },
        submitForm() {
          // Gérez la soumission du formulaire ici
          // Par exemple : this.text contient le texte entré dans le textarea
          // Vous pouvez envoyer les données au serveur ou effectuer d'autres actions.
        },
      },
    });
  </script>
</body>
</html>
```

Dans cet exemple, nous utilisons Vue.js pour gérer le textarea et les événements. Lorsque l'utilisateur appuie sur "Entrée" dans le textarea, l'événement est intercepté par `@keydown.enter.prevent="addNewLine"` pour ajouter un saut de ligne à la valeur du textarea, et `@submit.prevent="submitForm"` empêche la soumission du formulaire par défaut.

Assurez-vous d'inclure la bibliothèque Vue.js dans votre projet, comme indiqué dans la balise `<script>`.

### Recherche pour Axel

Bien sûr, voici un exemple d'un tableau avec une liste de lignes cliquables en utilisant Vue.js. Dans cet exemple, chaque ligne du tableau est une entrée cliquable qui affiche une alerte lorsque vous cliquez dessus :

```html
<!DOCTYPE html>
<html>
<head>
  <title>Tableau avec des lignes cliquables en Vue.js</title>
</head>
<body>
  <div id="app">
    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>Nom</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in items" :key="item.id" @click="showAlert(item.name)">
          <td>{{ item.id }}</td>
          <td>{{ item.name }}</td>
          <td>
            <button @click.stop="editItem(item.id)">Editer</button>
            <button @click.stop="deleteItem(item.id)">Supprimer</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14"></script>
  <script>
    new Vue({
      el: '#app',
      data: {
        items: [
          { id: 1, name: 'Article 1' },
          { id: 2, name: 'Article 2' },
          { id: 3, name: 'Article 3' },
        ],
      },
      methods: {
        showAlert(name) {
          alert('Vous avez cliqué sur : ' + name);
        },
        editItem(id) {
          alert('Édition de l'élément avec l'ID : ' + id);
        },
        deleteItem(id) {
          alert('Suppression de l'élément avec l'ID : ' + id);
        },
      },
    });
  </script>
</body>
</html>
```

Dans cet exemple, nous utilisons Vue.js pour générer le tableau et gérer les événements. Chaque ligne du tableau est générée à partir des données stockées dans `items`, et en cliquant sur une ligne, la méthode `showAlert` est appelée pour afficher une alerte avec le nom de l'élément correspondant. De plus, chaque ligne a des boutons "Éditer" et "Supprimer" qui déclenchent également des alertes. Vous pouvez personnaliser les actions à effectuer lorsque vous cliquez sur une ligne ou un bouton en modifiant les méthodes correspondantes.

### Pour Nicole

Voici un exemple d'un champ `input` de type `number` en Vue.js qui empêche la saisie d'une valeur inférieure à 5 et qui a une note minimum de 5 :

```html
<!DOCTYPE html>
<html>
<head>
  <title>Champ input de type number avec note minimum en Vue.js</title>
</head>
<body>
  <div id="app">
    <label for="note">Note (minimum 5) :</label>
    <input type="number" id="note" v-model.number="userNote" @input="validateNote" min="5">
    <p v-if="userNote < 5" style="color: red;">La note ne peut pas être inférieure à 5.</p>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/vue@2.6.14"></script>
  <script>
    new Vue({
      el: '#app',
      data: {
        userNote: 5,
      },
      methods: {
        validateNote() {
          if (this.userNote < 5) {
            this.userNote = 5; // Réinitialise à 5 si la valeur est inférieure
          }
        },
      },
    });
  </script>
</body>
</html>
```

Dans cet exemple, nous utilisons `v-model.number` pour lier la valeur de l'`input` à la variable `userNote` en tant que nombre. L'attribut `min="5"` est également utilisé pour définir la note minimale à 5. Si l'utilisateur essaie de saisir une note inférieure à 5, une validation est effectuée dans la méthode `validateNote`, qui réinitialise la valeur à 5. Une alerte d'erreur est affichée en rouge si la note est inférieure à 5 grâce à la directive `v-if`.