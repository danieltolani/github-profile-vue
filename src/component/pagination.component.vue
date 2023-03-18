<template>
    <div class="paginate">
        <button @click="onPageChange(currentPage - 1)"
        activeClass="active"
        >Prev</button>
        <button v-for="page in pages" :key="page" @click="onPageChange(page)"
        activeClass="active"
        >{{ page
        }}</button>
        <button @click="onPageChange(currentPage + 1)"
        activeClass="active"
        >Next</button>
    </div>
</template>

<script>
import { computed } from 'vue'

export default {
    name: 'PaginationComponent',
    props: {
        totalPages: {
            type: Number,
            required: true
        },
        perPage: {
            type: Number,
            required: true
        },
        currentPage: {
            type: Number,
            required: true
        }
    },
    emits: ['pagechanged'],
    setup(props, { emit }) {
        const pages = computed(() => {
            const pages = []

            for (let i = 1; i <= props.totalPages; i++) {
                pages.push(i)
            }

            return pages
        })

        const onPageChange = (page) => {
            if (page < 1 || page > props.totalPages) return

            emit('pagechanged', page)
        }

        return {
            pages,
            onPageChange
        }
    }
}
</script>

<style lang="scss" scoped>
.paginate {
    display: flex;
    justify-content: center;
    margin: 2rem 0;

    button {
        margin: 0 1rem;
        border: none;
        border-radius: 5px;
        background-color: #083042;
        color: #083042;
        cursor: pointer;


        // margin: auto;
        border: 1px solid #083042;
        padding: 1em 1.3em;
        font-size: 1rem;
        display: flex;
        align-items: center;
        margin-top: 2.5em;
        background-color: transparent;
        font-family: 'integral';
        cursor: pointer;

        &:hover {
            background-color: #083042;
            color: #ffffff;
            border: none;
        }

        &.active {
            background-color: #fff;
            color: #083042;
            border: 1px solid #083042;
        }
    }

    @media screen and (max-width: 768px) {
        flex-wrap: wrap;
        
        button {
            margin: 1rem;
        }
    }
}
</style>