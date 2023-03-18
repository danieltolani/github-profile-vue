<template>
    <div class="repos">
        <h1>Repos</h1>
        <ul>
            <li v-for="repo in repoData.slice((currentPage - 1) * perPage, currentPage * perPage)" :key="repo.id">
                <a :href="repo.html_url" target="_blank">{{ repo.name }}</a>
            </li>
        </ul>
        <Pagination :totalPages="totalPages" :perPage="perPage" :currentPage="currentPage" @pagechanged="onPageChange" />
    </div>
</template>

<script>
import Pagination from './pagination.component.vue'
import { ref } from 'vue'

const repoData = ref([])
const currentPage = ref(1) 
const perPage = ref(5)
const totalPages = ref(0)

export default {
    name: 'RepoData',
    components: {
        Pagination
    },
    setup () {
        fetch('https://api.github.com/users/danieltolani/repos')
            .then(res => res.json())
            .then(data => {
                repoData.value = data
                totalPages.value = Math.ceil(repoData.value.length / perPage.value)
            })

        return {
            repoData,
            currentPage,
            perPage,
            totalPages
        }
    },
    methods: {
        onPageChange (page) {
            currentPage.value = page
        }
    }
}
</script>

<style lang="scss" scoped>
.repos {
    h1 {
        text-align: center;
        font-family: 'integral';
        font-size: 2rem;
        color: #083042;
        margin: 2rem 0;
        font-weight: 400;
    }

    ul {
        list-style: none;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        flex-direction: column;

        li {
            margin: 1rem;
            background-color: #fff;
            padding: 1rem;
            border-radius: 5px;
            border: 1px solid #0830422d;
            cursor: pointer;

            &:hover{
                background: #083042;
                color: #ffffff;

                a{
                    color: #ffffff;
                    font-size: 1.6rem;
                }
            }

            a {
                text-decoration: none;
                color: #083042;
                font-size: 1.5rem;
            }
        }
    }
}</style>