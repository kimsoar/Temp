<template>
    <div class="tg-item">
        <input class="tgl tgl-skewed" id="toggle" type="checkbox" :checked="value" @input="updateValue" />
        <label class="tgl-btn" :data-off-text="offText" :data-on-text="onText" :style="{
          '--off-background-color': offBackgroundColor,
          '--on-background-color': onBackgroundColor,
          '--font-color': fontColor
        }" 
        for="toggle"></label>
    </div>
</template>

<script>
    export default {
        props: {
            value: {
              type: Boolean,
              default: false
            },
            offText: {
                type: String,
                default: 'Off'
            },
            onText: {
                type: String,
                default: 'On'
            },
            // offBackgroundColor: {
            //   type: String,
            //   default: '#888'
            // },
            // onBackgroundColor: {
            //   type: String,
            //   default: '#86d993'
            // }
        },
        data() {
          return {
            valueModel: this.value,
            offBackgroundColor: '#888',
            onBackgroundColor: '#86d993',
            fontColor: '#FFF'
          }
        },
        methods: {
          updateValue(event) {
            this.$emit('input', event.target.checked)
         }
        }
    }
</script>

<style lang="scss" scoped>
.tg-item {
  margin: 0 2em;
}

.tgl {
  display: none;
  &,
  &:after,
  &:before,
  & *,
  & *:after,
  & *:before,
  & + .tgl-btn {
    box-sizing: border-box;
    &::selection {
      background: none;
    }
  }
  
  + .tgl-btn {
    font-size-adjust: 0.58;
    outline: 0;
    display: block;
    width: 4em;
    height: 2em; 
    position: relative;
    cursor: pointer;
    user-select: none;
    &:after,
    &:before {
      position: relative;
      display: block;
      content: "";
      width: 50%;
      height: 100%;
    }
    
    &:after {
      left: 0;
    }
    
    &:before {
      display: none;
    }
  }
  
  &:checked + .tgl-btn:after {
    left: 50%;
  }
}

.tgl-skewed {
  + .tgl-btn {
    border-radius: 10px;
    overflow: hidden;
    backface-visibility: hidden;
    transition: all .2s ease;
    font-family: sans-serif;
    /* background: #888; */
    background: var(--off-background-color);
    &:after,
    &:before {
      display: inline-block;
      transition: all .2s ease;
      width: 100%;
      text-align: center;
      position: absolute;
      line-height: 2em;
      font-weight: bold;
      /* color: #fff; */
      color: var(--font-color);
      text-shadow: 0 1px 0 rgba(0,0,0,.4);
    }
    
    &:after {
      left: 100%;
      content: attr(data-on-text);
    }
    
    &:before {
      left: 0;
      content: attr(data-off-text);
    }
    
    &:active {
      /* background: #888; */
      background: var(--off-background-color);
      &:before {
        left: -10%;
      }
    }
  }
  
  &:checked + .tgl-btn {
    /* background: #86d993; */
    background: var(--on-background-color);
    &:before {
      left: -100%;
    }

    &:after {
      left: 0;
    }

    &:active:after {
      left: 10%;
    }
  }
}

</style>