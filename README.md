# NotePadLifecycle

**NotePadLifecycle** est une application mobile Android de prise de notes développée en **Kotlin**. Elle met l’accent sur la gestion optimale du cycle de vie des composants grâce aux **Android Lifecycles**. L’application permet à l’utilisateur de créer, modifier et supprimer des notes directement depuis une interface intuitive.

## Fonctionnalités

- ✏️ **Créer une note**  
  Saisissez un titre et un contenu pour ajouter une nouvelle note.

- 📝 **Modifier une note**  
  Sélectionnez une note existante pour en éditer le contenu et sauvegarder les modifications.

- 🗑️ **Supprimer une note**  
  Effacez une note de la liste en un clic.

- ♻️ **Gestion du cycle de vie**  
  Utilisation des **ViewModel**, **LiveData**, et des observateurs de lifecycle pour garantir la persistance et l'intégrité des données lors des changements d'orientation, de la mise en arrière-plan, etc.

- 📋 **Interface intuitive**  
  Listes de notes avec possibilités d’ajout, modification et suppression rapides.

## Stack technique

- **Langage** : Kotlin
- **Architecture** : MVVM
- **Composants utilisés** :
  - ViewModel
  - LiveData
  - LifecycleObserver
  - RecyclerView
- **UI** : Jetpack Compose ou XML
- **Persistence** : In-memory (Simple) ou Room Database (pour stockage local)

## Aperçu de l’application

![Capture d’écran de NotePadLifecycle](screenshot.png)

## Utilisation

1. **Lancez l’application sur votre appareil Android**.
2. **Ajoutez une nouvelle note** via le bouton “+”.
3. **Appuyez sur une note** pour la modifier.
4. **Maintenez ou faites glisser** pour supprimer une note (selon l’implémentation).

## Exemple rapide d’utilisation de ViewModel et Lifecycle

```kotlin
class NoteViewModel(application: Application) : AndroidViewModel(application) {
    private val _notes = MutableLiveData<List<Note>>()
    val notes: LiveData<List<Note>> = _notes
    // fonctions pour ajouter, modifier, supprimer les notes...
}

class MainActivity : AppCompatActivity() {
    private val noteViewModel: NoteViewModel by viewModels()
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        // Observer le LiveData pour lister/mettre à jour les notes
        noteViewModel.notes.observe(this) { notes ->
            // Update UI here
        }
    }
}
