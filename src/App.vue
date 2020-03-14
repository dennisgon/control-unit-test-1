<template>
  <div id="app" class="container">
    <div class="row">
      <big-component-thumbnail v-if="datas.length > 0" :title="datas[0].title" :image="datas[0].image" :description="datas[0].desc"></big-component-thumbnail>
    </div>
    <div class="row">
      <div class="card-group">
        <component-thumbnail @click.native="changeData(index)" v-for="(data, index) in datas.slice(1)" :title="data.title" :image="data.image" :description="data.desc"></component-thumbnail>
      </div>
    </div>

    <div class="row">
      <div class="col-md-12">
        <form class="form-horizontal">
          <div class="form-group">
            <label for="title">title gambar</label>
            <input type="text" v-model="title" class="form-control" id="title" aria-describedby="titleHelp" placeholder="Enter title">
            <small id="titleHelp" class="form-text text-muted">title dari gambar yang akan disimpan</small>
          </div>
          <div class="form-group">
            <label for="description">description gambar</label>
            <textarea type="text" v-model="desc" class="form-control" id="description" aria-describedby="descriptionHelp" placeholder="Enter description"></textarea>
            <small id="descriptionHelp" class="form-text text-muted">description dari gambar yang akan disimpan</small>
          </div>
          <div class="form-group">
            <label for="image">image gambar</label>
            <input type="text" v-model="image" class="form-control" id="image" aria-describedby="imageHelp" placeholder="Enter image">
            <small id="imageHelp" class="form-text text-muted">url image dari gambar yang akan disimpan</small>
          </div>
          <button @click="addData" type='button' class="btn btn-primary">Submit</button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
  import thumbnail from './Components/Thumbnail.vue'
  import thumbnailBig from './Components/BigThumbnail.vue'

  export default {
    name: 'app',
    data () {
      return {
        datas :[],
        image:"",
        desc:"",
        title:"",
      }
    },
    components:{
      'component-thumbnail': thumbnail,
      'big-component-thumbnail': thumbnailBig
    },
    mounted:function(){
      this.initialized() 
    },
    methods:{
      addData(){
        let data={
          "title": this.title,
          "desc": this.desc,
          "image": this.image
        }
        this.datas.push(data);
        this.title="";
        this.desc="";
        this.image="";
      },
      changeData(index){
        index = index+1;
        let b = this.datas[0];
        this.datas.splice(0,0, this.datas[index]);
        this.datas.splice(index+1,1);
      },
      initialized(){
        let data={
          "title": "Kompas Digital 3 Rubrik",
          "desc": "Akses ke tiga rubrik favorit Anda (tidak termasuk ePaper).",
          "image": "https://gerai-kompas-id.azureedge.net/wp-content/uploads/2018/11/paket-Kompas-digital-3rubrik-1-416x505.jpg"
        }
        this.datas.push(data);
        let data1={
          "title": "Kompas Digital Premium",
          "desc": "Akses ke seluruh konten digital termasuk ePaper, tanpa batas.",
          "image": "https://gerai-kompas-id.azureedge.net/wp-content/uploads/2018/11/Produk-Kompas-Digital-Premium-494x600-1-416x505.png"
        }
        this.datas.push(data1);
        let data2={
          "title": "Kompas Digital Premium & Koran",
          "desc": "Akses ke seluruh konten digital, ePaper, dan Kompas cetak.",
          "image": "https://gerai-kompas-id.azureedge.net/wp-content/uploads/2018/12/Produk-Kompas-Digital-Koran-494x600-416x505.png"
        }
        this.datas.push(data2);
      }
    }
  }
</script>

<style>
</style>
