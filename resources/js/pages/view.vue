<template>
      <basic>

    <div class="pb-10">
    <v-app-bar
      color="white"
      app
      id="viewers"
    >
    <v-btn
    icon
    @click="goBack"
    >
      <v-icon>
          mdi-chevron-left
      </v-icon>
    </v-btn>
    <v-spacer></v-spacer>
      <v-toolbar-title
      class="h6" style="margin-top: 0.5rem;"
      >{{post.title}}
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn @click.stop="drawer = !drawer" icon><v-icon>mdi-magnify</v-icon></v-btn>
      <v-spacer></v-spacer>
      <span v-if="post.location != null" @click="browseLocation(post.location.slug)">
                  <v-icon color="success">
                    mdi-navigation
                  </v-icon>        
        {{post.location.location}}
      </span>
    </v-app-bar>
    <v-navigation-drawer
      v-model="drawer"
      app
      temporary
      class="bigtipper"
    >
    <v-app-bar>
      Search
      <v-spacer></v-spacer>
      <v-btn @click.stop="drawer = !drawer" icon><v-icon>mdi-close</v-icon></v-btn>
    </v-app-bar>
    <v-main>
      <search :flower="'mb-0 col-md-12'" />
    </v-main>


    </v-navigation-drawer>

  <v-container>
        <v-main>
      <v-breadcrumbs
      light
      divider=">>"
      class="px-1"
      >
        <v-breadcrumbs-item
        href="/"
        class="text-dark"
        >
          Home
        </v-breadcrumbs-item>
        <v-breadcrumbs-item
        disabled
        >
          Business
        </v-breadcrumbs-item>
        <v-breadcrumbs-item>
          {{post.title}}
        </v-breadcrumbs-item>      
      </v-breadcrumbs>
  <v-card flat>
  <v-row>
      <v-list-item class="grow">

        <v-list-item-content>
          <v-list-item-title class="font-weight-bold">About {{post.title}}
            <div class="container">
                  <v-row
                    align="center"
                  >
                    <v-rating
                      :value="post.rate"
                      dark
                      color="amber"
                      dense
                      half-increments
                      readonly
                      size="20"
                    ></v-rating>

                    <span class="grey--text ml-4">
                      4.5 (1)
                    </span>
                  </v-row>
            </div>

          </v-list-item-title>
        </v-list-item-content>

        <v-list-item-avatar color="grey darken-3">
          <v-img
            class="elevation-6"
            alt=""
            :src="'/storage/'+post.image"
          ></v-img>
        </v-list-item-avatar>
      </v-list-item>
    <v-card-text>
      <div class="body-2 text-primary">
        <template v-for="(category, index) in post.category">
          <template v-if="index > 0">
            ,
          </template>
          <a :key="index" :href="'/location/' + post.location.slug +'/category/' + category.slug">{{category.name}}</a>
        </template>
      </div>

      <div class="subtitle-2" v-text="post.excerpt"></div>
      <!-- <div>
    <v-tabs
      color="green darken-4"
      centered
    >
      <v-tab class="col">Landscape</v-tab>
      <v-tab class="col">Abstract</v-tab>

      <v-tab-item
        v-for="n in 2"
        :key="n"
      >
        <v-container fluid>
          <v-row>
  <v-bottom-navigation
    color="green"
    grow
  >
    <template v-if="post.company_number">
      <v-btn :href="'tel:'+post.company_number">
        <span>Call</span>

        <v-icon color="success">mdi-phone</v-icon>
      </v-btn>
    </template>
    <template v-if="post.company_number">
        <v-btn :href="'sms:'+post.company_number">
          <span>Text</span>

          <v-icon color="primary">mdi-message-text</v-icon>
        </v-btn>
    </template>

    <template v-if="post.whatsapp">
        <v-btn target="blank" :href="post.whatsapp">
          <span>Whatsapp</span>

          <v-icon color="success">mdi-whatsapp</v-icon>
        </v-btn>
    </template>

    <template v-if="post.company_email">
      <v-btn :href="'mailto:'+post.company_email">
        <span>Email</span>

        <v-icon color="red">mdi-email</v-icon>
      </v-btn>
    </template>
  </v-bottom-navigation>





            
          </v-row>
        </v-container>
      </v-tab-item>
    </v-tabs>        
      </div> -->





    <!-- <div>
      <ul class="nav nav-tabs justify-content-end">
        <li class="nav-item">
          <a href="#" class="nav-link active">
            Reviews
          </a>
        </li>
      </ul>
      <div class="tab-content">
        <div class="tab-pane active">
          <v-row>
          <v-col sm="12" md="6" lg="4">
            <v-card>
              <v-card-text>
                <b>Foody
                  
                </b>
              <v-rating
                :value="post.rate"
                dark
                small
                color="amber"
                dense
                half-increments
                readonly
                size="20"
              ></v-rating>
              
                An onliine food delivery network situated at gregory university uturu
              </v-card-text>
            </v-card>
          </v-col>
          <v-col sm="12" md="6" lg="4">
            <v-card>
              <v-card-text>
                <b>Foody
                  
                </b>
              <v-rating
                :value="post.rate"
                dark
                small
                color="amber"
                dense
                half-increments
                readonly
                size="20"
              ></v-rating>
              
                An onliine food delivery network situated at gregory university uturu
              </v-card-text>
            </v-card>
          </v-col>
          <v-col sm="12" md="6" lg="4">
            <v-card>
              <v-card-text>
                <b>Foody
                  
                </b>
              <v-rating
                :value="post.rate"
                dark
                small
                color="amber"
                dense
                half-increments
                readonly
                size="20"
              ></v-rating>
              
                An onliine food delivery network situated at gregory university uturu
              </v-card-text>
            </v-card>
          </v-col>
          </v-row>


        </div>

      </div>
    </div> -->
      
      <v-divider></v-divider>
      <v-row>
  <v-bottom-navigation
    color="green"
    grow
  >
    <template v-if="post.company_number">
      <v-btn :href="'tel:'+post.company_number">
        <span>Call</span>

        <v-icon color="success">mdi-phone</v-icon>
      </v-btn>
    </template>
    <template v-if="post.company_number">
        <v-btn :href="'sms:'+post.company_number">
          <span>Text</span>

          <v-icon color="primary">mdi-message-text</v-icon>
        </v-btn>
    </template>

    <template v-if="post.whatsapp">
        <v-btn target="blank" :href="post.whatsapp">
          <span>Whatsapp</span>

          <v-icon color="success">mdi-whatsapp</v-icon>
        </v-btn>
    </template>

    <template v-if="post.company_email">
      <v-btn :href="'mailto:'+post.company_email">
        <span>Email</span>

        <v-icon color="red">mdi-email</v-icon>
      </v-btn>
    </template>
  </v-bottom-navigation>

      </v-row>
      
    </v-card-text>
    
    <v-divider class="mx-4"></v-divider>
    <v-card-text class="h6 font-weight-bold" v-if="deals_with.length > 0">
        Deals with:
              <v-chip-group
        active-class="black white--text"
        column
      >
        <template  v-for="(deals, i) in deals_with">
          <div  :key="i">
        <v-chip v-if="post.location != null" class="text-capitalize" :href="'/search/'+post.location.slug+
        '/'+textToSlug(deals.trim())">{{deals.trim()}}</v-chip>
        <v-chip v-else>{{deals}}</v-chip>
          </div>
        </template>
      </v-chip-group>

    </v-card-text>
    <!-- <v-divider class="mx-4"></v-divider> -->
    <!-- <v-card-text>
      <div>
      <v-btn small outlined color="success">Reviews</v-btn>
      </div>
      <v-card>
          
        <v-card-title class="h6">
          From a star
        </v-card-title>
        <v-card-subtitle>
          This service is so nice... I might use them again in the future.
        </v-card-subtitle>
      </v-card>
    </v-card-text> -->
</v-row>
  </v-card>
      <!-- Embedded Page  -->
        <v-row>
          <v-col>
        <v-sheet class="bigtippers">

              
              <div class="postbody" v-if="post.body">
                
                <v-card>
                  <v-card-subtitle class="font-italic">
                    Description
                  </v-card-subtitle>
                  <v-card-text v-html="post.body">
                    
                  </v-card-text>
                </v-card>
              </div>
              <div class="instagram" v-if="post.instagram_page">
                <v-card>
                  <v-card-subtitle class="text-black-50">
                    Instagram 
                  </v-card-subtitle>
                    <instagram-embed
                      :url="post.instagram_page"
                    />
                </v-card>
                <hr>

              </div>
              <div class="facebook" v-if="post.facebook_page">
                <v-card>
                  <v-card-subtitle class="text-black-50">
                    Facebook
                  </v-card-subtitle>
                  <div v-html="post.facebook_page">

                  </div>
                </v-card>
                <hr>
              </div>
              <div class="twitter" v-if="post.twitter_page">
                <v-card>
                  <v-card-subtitle class="text-black-50">
                    Twitter
                  </v-card-subtitle>
                  <div v-html="post.twitter_page">

                  </div>

                </v-card>
              </div>

              
            </v-sheet>
          </v-col>
        </v-row>
        <!-- Reach Out -->
        <v-row>
            <v-card
          outlined
          class="col-12 bottom-0"
          flat
        >
            <v-card-title class="h6 my-0">
              Profiles
            </v-card-title>
          <!-- References -->
          <v-row>
            <v-card class="col-12" flat>
              <v-card-actions class="col-12 py-0">
              <div class="row row-sm align-items-center">
                <div class="col text-center" v-if="post.link != null">
                  <v-btn rounded class="text-text-decoration-none" target="blank" :href="'https://'+post.link">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z"></path><circle cx="12" cy="12" r="9"></circle><line x1="3.6" y1="9" x2="20.4" y2="9"></line><line x1="3.6" y1="15" x2="20.4" y2="15"></line><path d="M11.5 3a17 17 0 0 0 0 18"></path><path d="M12.5 3a17 17 0 0 1 0 18"></path></svg>
                    Website

                  </v-btn>
                </div>
                <div class="col text-center" v-if="post.instagram != null">
                  <v-btn rounded class="text-text-decoration-none" target="blank" :href="'https://www.instagram.com/'+post.instagram">
                    <v-icon color="pink darken-1">mdi-instagram</v-icon>
                    Instagram

                  </v-btn>
                </div>              
                <div class="col text-center" v-if="post.twitter != null">
                  <v-btn class="text-text-decoration-none" rounded target="blank" :href="'https://www.twitter.com/'+post.twitter">
                    <v-icon color="light-blue lighten-3">mdi-twitter</v-icon>
                    Twitter

                  </v-btn>
                </div>              
                <div class="col text-center" v-if="post.facebook != null">
                  <v-btn rounded class="text-text-decoration-none" target="blank" :href="'https://www.facebook.com/'+post.facebook">
                    <v-icon color="indigo">mdi-facebook</v-icon>
                    Facebook

                  </v-btn>
                </div>              
                <div class="col text-center" v-if="post.whatsapp != null">
                  <v-btn class="text-text-decoration-none" target="blank" rounded :href="post.whatsapp">
                    <v-icon color="success">mdi-whatsapp</v-icon>
                    WhatsApp

                  </v-btn>
                </div>              


              </div>
                  
                
              </v-card-actions>
            </v-card>

          </v-row>
        <v-divider></v-divider>

            <v-card-actions>
              <v-responsive>
            <v-list
            class="dvvv"
            two-line>
            <template v-if="post.company_number != null">

              <v-list-item :href="'tel:'+post.company_number">
                <v-list-item-icon>
                  <v-icon color="indigo">
                    mdi-phone
                  </v-icon>
                </v-list-item-icon>

                <v-list-item-content>
                  <v-list-item-title v-text="post.company_number"></v-list-item-title>
                  <v-list-item-subtitle>Mobile</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
              <v-divider inset></v-divider>
            </template>
            <template v-if="post.company_email != null">
              <v-list-item :href="'mailto:'+post.company_email">
                <v-list-item-icon>
                  <v-icon color="indigo">
                    mdi-email
                  </v-icon>
                </v-list-item-icon>

                <v-list-item-content>
                  <v-list-item-title v-text="post.company_email"></v-list-item-title>
                  <v-list-item-subtitle>Mail</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>

              <v-divider inset></v-divider>


            </template>
              <template v-if="post.company_address != null">
              <v-list-item target="blank"  :href="'http://maps.google.com/?q='+ post.company_address">
                <v-list-item-icon>
                  <v-icon color="indigo">
                    mdi-map-marker
                  </v-icon>
                </v-list-item-icon>

                <v-list-item-content>
                  <v-list-item-title>{{post.company_address}}</v-list-item-title>
                  <v-list-item-subtitle>Address</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
              <v-divider inset></v-divider>

              </template>
              <template v-if="post.company_full_name != null">
              <v-list-item>
                <v-list-item-icon>
                  <v-icon color="indigo">
                    mdi-office-building
                  </v-icon>
                </v-list-item-icon>

                <v-list-item-content>
                  <v-list-item-title>{{post.company_full_name}}</v-list-item-title>
                  <v-list-item-subtitle>Business Name</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
              <v-divider inset></v-divider>
              </template>
              <template v-if="post.owner_of_business != null">
              <v-list-item>
                <v-list-item-icon>
                  <v-icon color="indigo">
                    mdi-account-key
                  </v-icon>
                </v-list-item-icon>

                <v-list-item-content>
                  <v-list-item-title>{{post.owner_of_business}}</v-list-item-title>
                  <v-list-item-subtitle>Founder</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
              </template>


            </v-list>
              </v-responsive>
            </v-card-actions>
        </v-card>

        </v-row>
        </v-main>

  </v-container>
  <v-container>
    <v-col>
    <h5 class="font-weight-bold">See Related businessess</h5>
    <v-row>
      <v-col cols="12" sm="4" v-for="(relative, i) in relatives" :key="i">
  <v-card
    :href="'/business/'+relative.slug"
  >
    <v-list-item three-line>
      <v-list-item-content>
        <div class="text-overline mb-3">
          <v-icon color="success">mdi-navigation</v-icon>
          {{relative.location.location}}
        </div>
        <v-list-item-title class="">
          {{relative.title}}
        </v-list-item-title>
        <!-- <v-list-item-subtitle>Greyhound divisely hello coldly fonwderfully</v-list-item-subtitle> -->
      </v-list-item-content>

      <v-list-item-avatar
        tile
        size="80"
      >
          <v-img
            class="elevation-6"
            alt=""
            :src="'/storage/'+relative.image"
          ></v-img>
      </v-list-item-avatar>
    </v-list-item>


  </v-card>



      </v-col>
    </v-row>
    </v-col>
  </v-container>
  <span class="container-fluid">
    <a href="/"> <v-icon>mdi-arrow-left</v-icon> Return to homepage</a>
  </span>
    </div>
      </basic>
</template>
<script>
import Search from '..//components/HomeSearch'
import Basic from '..//layouts/basic'
import InstagramEmbed from 'vue-instagram-embed';

export default {
   
    props: ['slug'],
    components: {
      Search,
      Basic,
      InstagramEmbed
    },
    data() {
      return {
        post: '',
        dialog: false,
        rating: 0,
        tab: null,
        deals_with: [],
        drawer: null,
        relatives: '',
      }
    },
    created() {
      this.getPost();
    },
    methods: {
      getPost() {
        axios.get('/api/post/'+this.slug)
            .then((response)=>{
                this.post = response.data.post;
                this.relatives = response.data.relatives;
                var deals_get = response.data.post.deals_with;
                var str_array = deals_get.split(',');
                this.deals_with = str_array;
            }).catch(err => {
                // alert('Please Reload');
                // location.reload();

            });    
        
      },
      goBack(){
          window.history.back();
      },
      textToSlug(Text) {
        return Text
          .toLowerCase()
          .trim()
          .split(' ')
          .join('-');
      },
      browseLocation(slug) {
        window.location= '/browse-location/'+ slug;
      }

    },
    mounted() {
      var plug = document.createElement("script");
      plug.setAttribute(
        "src", "//s7.addthis.com/js/300/addthis_widget.js#pubid=ra-5ec45c28a73184d6"
      );
      plug.type = "text/javascript";
      document.head.appendChild(plug);
    },
}
</script>
<style scoped>
.dvvv{
  overflow-x: scroll !important;
}
.bigtippers{
  overflow-y: scroll !important;
  height: 350px !important;
  border-top: 1px solid rgba(0,0,0,.12);
}
#viewers .v-toolbar__content {
    padding-right: 0 !important;
}
.bigtipper {
  width: 350px !important;
}
@media screen and (max-width: 760px){
  .bigtipper{width: 100vw !important; margin: 0;}
}
</style>