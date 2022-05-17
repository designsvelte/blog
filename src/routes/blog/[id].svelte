<script context="module">
    export const load = async ({params, fetch}) => {
        console.log(params);
        const id = params.id
        const res = await fetch(`https://jsonplaceholder.typicode.com/posts/${id}`);

        const post = await res.json();
        
        return {
            props: {
                post,
            }
        }
    }
</script>
<script>
    export let post;
</script>

<!-- {JSON.stringify(post)} -->
        <div class="post">
            <h1>{post.title}</h1>
            <p>{post.body}</p>
            <p class="dahafazla"><a href={`/`}>Bloga dön</a></p>
        </div>

<style>
    .post{
        border: 1px solid #ddd;
        padding: 10px;
        box-shadow: 0 0 10px #eee;
    }
    h1{
        margin:0;
    }
</style>
