<script setup></script>

<template>
    <form action="#" class="">
        <label for="status">Status:</label>
        <select id="statuses" name="statuses">
            <option value="All">All</option>
            <option value="Alive">Alive</option>
            <option value="Dead">Dead</option>
            <option value="Unknown">Unknown</option>
        </select>
        <label for="gender">Gender:</label>
        <select id="genders" name="genders">
            <option value="All">All</option>
            <option value="Alive">Male</option>
            <option value="Dead">Female</option>
            <option value="Genderless">Genderless</option>
            <option value="Unknown">Unknown</option>
        </select>
        <input type="search" placeholder="search for a character">
        <button>Search</button>
    </form>

</template>


<style scoped>
form{
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
    padding: 2rem;
}
select, input{
    border-radius: 8px;
    padding: 5px;
    border: 1px solid rgb(9, 71, 9);
}
button{
    padding: 5px 20px;
    border-radius: 8px;
    border: 1px solid rgb(9, 71, 9);
    background-color: rgba(184, 221, 35, 0.6);
    cursor: pointer;
}
</style>
