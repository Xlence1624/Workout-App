<script setup>
</script>

<template>
  <header>
    <p class="text-gradient text-3xl ">Xlen Fitness</p>
  </header>
  <main>
    <slot />
 
  </main>
  <footer>
    <small>Created by</small>
    <a href="#" target="_blank">
<img src="https://scontent.flos1-2.fna.fbcdn.net/v/t39.30808-6/270359909_631088548088505_2113682070889294724_n.jpg?_nc_cat=101&ccb=1-7&_nc_sid=6ee11a&_nc_eui2=AeEHkLtqUbHbBBcDqhwsLNDJP-srFvQu5go_6ysW9C7mCqUpJE__HyL9GVEm10J7qA--D-oLFzlLJgejjLmSW0DI&_nc_ohc=MYLeojS0z5kQ7kNvwHzkS1R&_nc_oc=AdnqLSP1klFaBrASbcOApBy1baseeYwZAjEu7TkeseSgW6fzSCxc8YDEk28B22mSY2k&_nc_zt=23&_nc_ht=scontent.flos1-2.fna&_nc_gid=Z_DR5IY1Oo5MntChIml5KA&oh=00_AfVNjWWv6vq5jVvEoZgFQ3RPcdRunr-4K4W36e-A1r15eQ&oe=689E48F6" alt="">
<p>Orji Michael</p>
<i class="fa-brands fa-github"></i>
    </a>
  </footer>
</template>

<style scoped>
header, footer, main{
  padding: 1rem;
  width: 100%;
  max-width: 600px;
  margin:  0 auto ;
}

main{
  flex: 1;
}
footer{
  display: flex;
  flex-direction: column ;
  gap: .5rem;
  align-items: center;
  padding:  2rem 0;
  padding-bottom:  3rem;
}
 footer a {
  display: flex;
  
  align-items: center;
color: black;
font-size: 13px;

  background: var(--background-muted);
  padding: 0.3rem;
  padding-right: 0.5rem;
  gap: 0.5rem;
  border-radius: 4rem;
border: solid 1px transparent;
transition-duration:  200ms;
text-decoration: none;

 }
footer a:hover{
  border: solid 1px var(--color-link);
  color: blue;
}
 footer a img{
  max-width: 30px;
  aspect-ratio: 1 / 1;
  border-radius: 100%;
  object-fit: cover;
  object-position: top;
 }
</style>