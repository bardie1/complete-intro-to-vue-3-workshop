<script>
export default {
    props: {
        title: {
            type: String,
            required: true
        },
        characterList: {
            type: Array,
            required: true
        },
    },
    emits: ['toggle-favourite'],
    computed: {
        characterCount() {
            return this.characterList.length;
        }
    }
}
</script>

<template>
    <h2>{{ title }} ({{ characterCount }})</h2>
   <ul>
        <li v-for="character in characterList" :key="character.name">
          <strong>{{ character.name }}</strong> - {{ character.role }}
          <button v-if="character.isFavourite"
            @click="$emit('toggle-favourite', character.name)">Unfavourite</button>
          <button v-else
            @click="$emit('toggle-favourite', character.name)">Favourite</button>
        </li>
    </ul>
</template>