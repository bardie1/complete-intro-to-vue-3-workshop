<script>
export default {
    emits: ["submit-form"],
    data() {
        return {
            newCharacterName: "",
            newCharacterRole: ""
        }
    },
    methods: {
        addCharacter() {
            this.$emit("submit-form", this.newCharacterName, this.newCharacterRole);
            this.newCharacterName = "";
            this.newCharacterRole = "";
        }
    }
}
</script>

<template>
  <div>
    <label for="characterName">Character Name</label>
    <input type="text" id="characterName" v-model="newCharacterName" />
    <label for="characterRole">Character Role</label>
    <input type="text" id="characterRole" v-model="newCharacterRole" />
    <button @click="addCharacter">Add Character</button>
  </div>
</template>