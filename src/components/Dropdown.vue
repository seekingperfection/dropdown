<template>
<div class="dropdown">
    <div class="dropdown-item" v-for="(item, index) in items" :key="index">
        <label class="container">{{ item }}
            <input :id="index" type="checkbox" v-model="checkedItems" :value="item">
            <span class="checkmark"></span>
        </label>
    </div>
    <span class="hide">{{ check }}</span>
</div>
</template>
<script>
export default {
    name: "Dropdown",
   
    data() {

        return {
            checkedItems: [],
            items: [
                "Customers",
                "VIP", 
                "Oldtimer",
                "Remove"
            ],
        }
    },
    computed: {
       check() {
            // let prev = this.checkedItems.length;
           this.$emit('updated', this.checkedItems.length)
           if(this.checkedItems.length == 0){
            console.log('sth bad')
           }
           return this.checkedItems.length;
       }
    }
}
</script>
<style lang="scss">
.dropdown {
    border: 1px solid #cccccc;
    border-radius: 6px;
    -webkit-box-shadow: 0px 0px 4px -1px #cccccc; 
    box-shadow: 0px 0px 4px -1px #cccccc;

    .dropdown-item {
        padding: 15px 10px;
        border-bottom: 1px solid #cccccc;
    }

    .dropdown-item:last-of-type {
        border: none;
    }

    .container {
        font-weight: 400;
    }
}

</style>