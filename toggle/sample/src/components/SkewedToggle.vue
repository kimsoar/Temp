<template>
    <div class="tg-item">
        <input class="tgl tgl-skewed" id="toggle" type="checkbox" v-model="value"/>
        <label class="tgl-btn" :data-off-text="offText" :data-on-text="onText" for="toggle"></label>
    </div>
</template>

<script>
    export default {
        props: {
            offText: {
                type: String,
                default: 'Off'
            },
            onText: {
                type: String,
                default: 'On'
            }
        },
        data() {
          return {
            value: false
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
    background: #888;
    &:after,
    &:before {
      display: inline-block;
      transition: all .2s ease;
      width: 100%;
      text-align: center;
      position: absolute;
      line-height: 2em;
      font-weight: bold;
      color: #fff;
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
      background: #888;
      &:before {
        left: -10%;
      }
    }
  }
  
  &:checked + .tgl-btn {
    background: #86d993;
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