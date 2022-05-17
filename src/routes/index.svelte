<script context="module">
    export const load = async ({ fetch }) => {
        const res = await fetch ('https://jsonplaceholder.typicode.com/posts');
        const posts = await res.json();
        return{
            props:{
                posts,
            }
        }
    }
</script>
<script>
    export let posts;
</script>

<h1>Post</h1>

<!-- {JSON.stringify(posts)} -->
<div class="posts">
    {#each posts as item, i}
        <div class="post">
            <h2>{item.title.substring(0,20)}</h2>
            <p>{item.body.substring(0,80)}</p>
            <p class="dahafazla"><a sveltekit:prefetch href={`/blog/${item.id}`}>Devamını Oku</a></p>
        </div>
        
    {/each}
</div>

<style>
    .posts{
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }
    .post{
        border: 1px solid #ddd;
        padding: 10px;
        box-shadow: 0 0 10px #eee;
    }
    h2{
        margin:0;
    }
    .dahafazla{
        text-align: right;
    }
</style>
