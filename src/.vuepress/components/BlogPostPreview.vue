<script>
export default {
    name: 'BlogPostPreview',
    props: {
        item: {
            type: Object,
            required: true
        }
    },
    computed: {
        formatPublishDate() {
            const dateFormat = new Date(this.item.frontmatter.date)
            const options = {
                year: 'numeric',
                month: 'long',
                day: 'numeric'
            } 

            return dateFormat.toLocaleDateString('en-US', options)
        }
    }
}
</script>

<template>
    <a :href="item.path">
        <img :src="'/blogHeaderImages/' + item.frontmatter.photo">
        <div>
            <h3 class="blog-post__title">{{ item.frontmatter.title }}</h3>
            <!-- <p v-if="item.frontmatter.excerpt">{{ item.frontmatter.excerpt }}</p> -->
            <time>{{ formatPublishDate }}</time>
        </div>
    </a>
</template>

<style scoped>
.blog-post__button {
	margin-bottom: 1.5rem;
	display: inline-block;
}

.blog-post__title {
	margin-top: 0.5rem;
}

.button {
	border: 1px solid #FFF238;
	border-radius: 4px;
	color: #FFF238;
	font-size: 0.8rem;
	padding: 0.5rem 0.75rem;
	text-transform: uppercase;
	font-weight: 700;
	box-shadow: 0 0;
	transition: background-color 0.2s ease-in, color 0.2s ease-in;
}

.tag-list {
    list-style: none;
    padding-left: 0;
    display: flex;
    margin-bottom: 25px;
}

.tag-list__item {
    margin-left: 10px;
}

.tag-list__item:first-child {
    margin-left: 0;
}

.tag-list__btn {
    padding: 5px;
    font-size: 0.9rem;
    background-color: #fff;
}

.post-container > a {
    box-shadow: 0 4px 6px 0 rgba(34, 34, 34, 0.2);
    cursor: pointer;
    background-color: #281552;
    color: #ddd;
}

.post-container > a:hover {
    box-shadow: 0 8px 12px 0 rgba(0, 0, 0, .8);
    text-decoration: none;
}

.post-container img {
    display: block;
    width: 100%;
    height: 15em;
    object-fit: cover;
}

.post-container div {
    padding: 1em;
    height: 7em;
}

.post-container h3 {
    color: white;
}
</style>
