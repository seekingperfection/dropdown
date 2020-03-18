<template>
    <div class="main__block">
        <div class="main__block--dropdown-block">
            <div class="main__block--dropdown-btn cursor"
            @click="toggleDropdown"
            v-click-outside="hide"
            :class="{active: isActive}">
                <span class="">Tag</span>
                <span class="main__block--count">{{checked}}</span>
                <span><font-awesome-icon icon="caret-down" /></span>
                <div class="show-dropdown">
                    <div v-if="!this.checked" class="main__block--error-block">
                        <span class="main__block--error">Please, select an option</span>
                    </div>
                    <dropdown @updated="changeHandler">
                    </dropdown>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Dropdown from './Dropdown';
import ClickOutside from 'vue-click-outside'

export default {
    name: "MainComponent",
    components: {
        Dropdown
    },
    directives: {
        ClickOutside
    },
    data(){
        return {
            isActive: false,
            checked: 0
        }
    },
    methods: {
        toggleDropdown() {
            this.isActive = !this.isActive;
        },
        hide(){
            this.isActive = false;
        },
        changeHandler(value) {
            
            this.checked = value;
            // if(this.checked < 1) {
            //     console.log('sth', this.checked);
              
            // }
            // console.log("this.checked = ");
            // console.log(this.checked);
            // let value = this.checkedItems;
            // return this.checkedItems;
            
        }
    },
    // computed: {
    //     check() {
    
    //     }
    // }


};
</script>

<style scoped lang="scss">
    .main__block {
        display: flex;
        // border: 1px solid red;
        height: 100vh;
        justify-content: center;
        align-items: center;

        .active {
            .show-dropdown {
                display:block;
                position:absolute;
                top: 34px;
                left: 50%;
                transform: translate(-50%, 0);
            }
        }

        .show-dropdown {
            display: none;
           
        }

        &--error-block {
            margin-bottom: 8px;
        }

        &--error {
            color: rgb(253, 0, 0,0.5);
            font-weight: 100;
            font-size: 0.6rem;
        }

        &--dropdown-block {
            // border: 1px solid red; 
            display: flex;
            justify-content: center;
            align-items: center;
            flex-flow: column;
            height: auto;

        }

        &--dropdown-btn {
            position: relative;
            display: flex;
            width: 80px;
            justify-content: space-around;
            padding: 5px 4px;
            border-radius: 6px;
            background-color: rgb(235, 235, 235);
            font-weight: bold;
            text-align: center;
            font-size: 0.9rem;
            align-items: center;
            color: rgb(70, 70, 70);
            // transition: 0.3s;
        }

        &--dropdown-btn:hover {
            border: 1px solid rgb(70, 70, 70);
        }

        &--count {

            background-color: rgb(70, 70, 70);
            padding: 2px 5px;
            border-radius: 4px;
            color: #ffffff;
            font-size: 0.8rem;

        }

    }
</style>
