<template>
  <div>
    <div> {{title}}</div>
    <ul>
      <li v-for="(product,index) in filteredProducts" :key="index">
        <ProductItem :product="product" :id="index" :addToShopCart="addToShopCart"/>
      </li>
    </ul>
    <div>Total a  pagar: ${{total}}</div>
  </div>
</template>

<script>
import ProductItem from './ProductItem.vue';
export default {
  name: 'HelloWorld',
  data () { 
    return { 
        title: 'My title',
        products:[
            {
              name: 'refrigerador',
              quantity: 0,
              price : 6000  
            }
            ,{
              name:'productos2',
              quantity: 5,
              price : 4000                
            }
            ,{
              name:'productos3',
              quantity: 6,
              price : 1000  
            }
            ,{
              name:'productos4',
              quantity: 2,
              price : 2000  
            }
            ,{
              name:'productos5',
              quantity: 3,
              price : 6000  
            }
          ],
          total :0 ,
          styleObject:
            {
            "bgColor":true,
            "txtColor":true,
            "bgColorBlue":false
            }

      }
  },
  computed :{
    filteredProducts(){
      return this.products.filter((products,index) => (index >= 3));
    }
  },
  methods:{
    changeToBgBlue(){
      console.log('cambiar color azul');
      this.styleObject.bgColor = false;
      this.styleObject.bgColorBlue = true;
    }
  },
  components:{
    ProductItem
  },
    methods:{
        addToShopCart(price){
            console.log('cambiar color azul');
            this.total += price;
    }
  } 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<!--style src="./css/style.css" scoped-->
<style scoped>
h3 {
    margin: 40px 0 0;
  }
ul {
list-style-type: none;
padding: 0;
}
li {
border: 1px solid black;
margin: 0 10px;
padding: 16px;
}
a {
color: #42b983;
}
/*.bgColor{
  background-color: #42b983;
}
.bgColorBlue{
  background-color: blue;
}
.txtColor{
  color: white;
}*/
</style>
