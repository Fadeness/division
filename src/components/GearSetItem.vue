<template>
  <div class="gear-item">
    <span
      class="gear-item-name"
      :class="[ isItemPossessed ? possessedClass : unpossessedClass]"
    >{{itemName}}</span>
    <br>
    <img
      @click="minusItem"
      class="gear-item-button"
      :class="[item.num > 0 ? '' : unpossessedButton]"
      src="../assets/images/minus.png"
    >
    <span class="gear-item-num">{{item.num}}</span>
    <img @click="addItem" class="gear-item-button" src="../assets/images/plus.png">
  </div>
</template>

<script>
import Store from './store.js'

export default {
    name: 'GearSetItem',
    props: {
        itemName: String
    },
    data() {
      return {
        possessedClass: 'gear-item-name--possessed',
        unpossessedClass: 'gear-item-name--unpossessed',
        unpossessedButton: 'gear-item-button--hide',
        item: {
          num: 0
        }
      }
    },
    mounted: function() {
      if(Store.fetch(this.$parent.gearTitle + ' '+ this.itemName)) {
        this.$set(this.item, 'num', Store.fetch(this.$parent.gearTitle + ' '+ this.itemName));
      }
    },
    methods: {
      addItem: function() {
        if(!this.isItemPossessed) {
          this.$emit('itemChange', 2);
        }
        this.item.num++;
        Store.save(this.$parent.gearTitle + ' '+ this.itemName, this.item.num);
      },
      minusItem: function() {
        if(this.item.num) {
          this.item.num--;
          if(!this.isItemPossessed) {
            this.$emit('itemChange', 0);
          }
        }
        Store.save(this.$parent.gearTitle + ' '+ this.itemName, this.item.num);
      }
    },
    computed: {
      isItemPossessed: function() {
        if(this.item.num > 0) {
          return true;
        } else {
          return false;
        }
      }
    }
}
</script>

<style>
.gear-item {
  font-size: 24px;
  font-weight: 500;
}
.gear-item-button {
  width: 18px;
  margin: 0 10px;
}
.gear-item-button--hide {
  opacity: 0;
}
.gear-item-name {
  transition: color 0.2s linear, text-shadow 0.2s linear;
}
.gear-item-name--unpossessed {
  color: rgb(153, 152, 152);
}
.gear-item-name--possessed {
  color: #fff;
  text-shadow: 0 0 5px #fff;
}
</style>
