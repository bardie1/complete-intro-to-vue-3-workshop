<script>
import CharacterList from "./components/CharacterList.vue";
import NewCharacterForm from "./components/NewCharacterForm.vue";
export default {
  components: {
    CharacterList,
    NewCharacterForm
  },
        data() {
          return {
            characterList: [
              { name: "Andy Dufresne", role: "Main Character", isFavourite: false },
              { name: "Ellis Boyd Redding", role: "Narrator", isFavourite: false },
              { name: "Warden Norton", role: "Antagonist", isFavourite: false },
              { name: "Tommy Williams", role: "Supporting Character", isFavourite: false },
              { name: "Samuel Norton", role: "Antagonist", isFavourite: false },
            ],
          }
        },
        computed: {
          favouriteCharacterList() {
            return this.characterList
              .filter((character) => character.isFavourite)
          },
        },
        methods: {
          toggleFavouriteCharacter(characterName) {
            this.characterList = this.characterList.map((character) => {
              if (character.name === characterName) {
                return {
                  ...character,
                  isFavourite: !character.isFavourite,
                };
              }
              return character;
            });
          },
          addCharacter(name, role) {
            this.characterList.push({
              name: name,
              role: role,
              isFavourite: false,
            });
          },
        }
      }
</script>

<template>
  <CharacterList title="Characters" :characterList="characterList" @toggle-favourite="toggleFavouriteCharacter" />
  <NewCharacterForm @submit-form="addCharacter" />
  <CharacterList title="Favourite Characters" :characterList="favouriteCharacterList" @toggle-favourite="toggleFavouriteCharacter" />
</template>