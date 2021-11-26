<template>
  <div>
    <nav>
      <PageNav />
    </nav>
    <header>
      <h1 class='text-center text-2xl'>{{ siteInfo.pageName }}</h1>
    </header>
    <main class="container flex mx-auto flex-col items-center">
      <section class=" w-max ">
      <Card :info="topic" v-for="topic in topics" :key="topic.id" />
      </section>
      <section>
        <h2>Tell Us What You Think</h2>
        <form @submit.prevent="addComment">
        <InputComment :value="message.msg" :inputInfo="message" v-model="message.msg" />
           <button class=" bg-gray-400">Add Comment</button>
        </form>
        <ul><li v-for="message in commentItems"
            :key="message.id"
            class="border-solid border-2 my-4">
            <p>{{message.msg}}</p>
            </li>
        </ul>
      </section>
    </main>
    <footer>
      <p>&copy; 2021 {{ siteInfo.author }}</p>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: {
        msg: '',
        label: 'Comment',
        inputName: 'input comment',
        comment: ''
      },
      siteInfo: {
        pageName: 'Recipes',
        author: 'Jessica'
      },
      topics: [
        {
          title: 'Hamburger Soup',
          image: 'image/hamburger-soup.jpg',
          description: 'A soup that will warm you up and fill you up all weather',
          difficulty: 'intermediate'
        },
        {
          title: 'Tomato Soup',
          image: 'image/tomato-soup.jpg',
          description: 'A delicious soup to be eaten for lunch or supper.',
          difficulty: 'Easy'
        },
        {
          title: 'Broccoli Soup',
          image: 'image/broccoli-soup.jpg',
          description: 'New take on an old favorite, this isnt your moms broccoli soup.',
          difficulty: 'Hard'
        }
      ],
      commentItems: []
    }
  },
  methods: {
    addComment: function() {
      console.log(this.message.msg)
      return this.commentItems.push({
        msg: this.message.msg
      })
    }
  }
}
</script>
