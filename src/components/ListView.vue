<template class="w-100">
  <div class="container" v-for="list in lists" :key="list.id">
    <!-- <router-link :to="{ name: 'listDetails', params: { id: list.id }}"> -->
      <div class="single">
        <div class="thumbnail">
          <img class="image" :src="list.image">
          <div class="tags">
            <ul>
              <li v-for="tag in list.tags" :key="tag">
                <img src="@/assets/tag.svg" />{{tag}}
              </li>
            </ul>
          </div>
        </div>
        <div class="info">
          
          <h3>{{ list.title }}</h3>
          <small>{{list.author}}</small>
          <p>{{list.summary}}</p>
          <span className="create-date">{{ new Date(list.create_date).toLocaleDateString("en-US", { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' }) }}</span>
        </div>
      </div>
    <!-- </router-link> -->
  </div>
</template>

<script>
export default {
  props: ['lists'],
}
</script>

<style scoped>
  .single {
    display: flex;
    border-radius: 2px;
    background: #f0f0f0;
    margin: 16px 0;
    transition: all ease 0.2s;
    width:100%;
    position: relative;
  }
  .single:hover {
    box-shadow: 1px 2px 3px rgba(50,50,50,0.05);
    transform: scale(1.02);
    transition: all ease 0.2s;
  }
  .thumbnail {
    width: 220px;
    height: 160px;
    flex:none;
    overflow: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
  }
  .single:hover .tags {
    top:0;
  }
  .thumbnail .tags {
    position: absolute;
    top:100%;
    left:0;
    right:0;
    height: 160px;
    transition: .4s all;
    overflow: hidden;
    background: linear-gradient(0deg,#383838 5%,rgba(51,51,51,0));
  }
  .thumbnail .tags ul {
    display: flex;
    flex-direction: column;
    width:120px;
    justify-content: flex-end;
    height: 100%;
    padding: 5px 10px;
  }
  .thumbnail .tags ul li {
    background-color: #00796b;
    color: #fff;
    padding: 4px 6px;
    border-radius: 5px;
    font-size: 10px;
    font-weight: bold;
    flex: none;
    margin-bottom: 5px;
    display: flex;
    align-items: center;

  }
  .thumbnail .tags ul li img {
    width:9px;
    margin-right: 6px;
  }
  .image {
    min-width: 100%;
    max-width: none;
    height: 100%;
    display: block;
    flex: none;
  }
  .info {
    margin-right: 30px;

    padding: 24px;
  }
  .info .create-date {
    text-align: right;
    width:100%;
    margin-top: 10px;
    display: block;
    font-size: 12px;
    color: #888;
    position: absolute;
    top: -5px;
    right: 10px;
  }
  .info small {
    color: #888;
  }
  .info h3 {
    margin-bottom: 5px;
    font-size: 18px;
    line-height: 22px;
  }
  .info p {
    margin-top: 5px;
    font-size: 14px;
    max-height: 36px;
    overflow: hidden;
  }
  
    @media (max-width: 800px) {
    .single{
      flex-direction: column;
    }
    .single .thumbnail{
      display: none;
    }
    .info {
      margin:0
    }
  .info h3 {
    margin-top: 0px;
    line-height: 22px;
  }
    }
</style>