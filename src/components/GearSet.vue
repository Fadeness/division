<template>
  <div class="gear">
    <h2 class="gear-title" :class="[gear.num == 6 ? collectedClass : '' ]">{{ gearTitle }}</h2>
    <GearSetItem @itemChange="checkPossession" item-name="Body Armor"></GearSetItem>
    <GearSetItem @itemChange="checkPossession" item-name="Backpack"></GearSetItem>
    <GearSetItem @itemChange="checkPossession" item-name="Gloves"></GearSetItem>
    <GearSetItem @itemChange="checkPossession" item-name="Knee Pads"></GearSetItem>
    <GearSetItem @itemChange="checkPossession" item-name="Masks"></GearSetItem>
    <GearSetItem @itemChange="checkPossession" item-name="Holsters"></GearSetItem>
  </div>
</template>

<script>
import GearSetItem from './GearSetItem.vue'
import Store from './store.js'

export default {
    name: 'GearSet',
    components: {
        GearSetItem
    },
    props: {
        gearTitle: String
    },
    data() {
      return {
        collectedClass: 'gear-title--collected',
        gear: {
          num: 0
        }
      }
    },
    mounted: function() {
      if(Store.fetch(this.gearTitle)) {
        this.$set(this.gear, 'num', Store.fetch(this.gearTitle));
      }
      
    },
    methods: {
      checkPossession(flag) { // 0, 减少; 1, 不变; 2, 增加
        if(flag === 0) {
          this.gear.num--;
        } else if(flag === 2) {
          this.gear.num++;
        }
        Store.save(this.gearTitle, this.gear.num);
      }
    }
}
</script>

<style>
.gear {
  padding: 40px 0;
  width: 50%;
  transition: all 0.2s linear;
}
@media all and (max-width: 768px) {
  .gear {
    width: 100%;
  }
}
.gear-title {
  margin: 0;
  margin-bottom: 20px;
  font-size: 28px;
  transition: text-shadow 0.2s linear;
}
.gear-title--collected {
  text-shadow: 0 5px 5px rgb(238, 69, 3);
}
</style>
