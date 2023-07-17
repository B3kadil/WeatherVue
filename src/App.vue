<script>
export default {

}
</script>

<template>
  <div class="wrapper">
      <h1>Погодное приложенме</h1>
      <p>Узнать погоду в вашем городе</p>
      <input type="text" name="" id="" placeholder="Введите название города">
      <button>Получить погоду</button>
  </div>
</template>

<style scoped>
.wrapper{
    width: 900px;
    height: 500px;
    border-radius: 50px;
    background: linear-gradient(135deg, #0044da, #9400b4);
    padding: 20px;
    color: #fff;
    text-align: center;
}
.wrapper h1{
    margin-top: 50px;
}
.wrapper p{
    margin-top: 20px;
}
.wrapper input{
    margin-top: 30px;
    background: transparent;
    border: 0;
    border-bottom: 2px solid #110813;
    color: #ffffff;
    font-size: 14px;
    padding: 5px 8px;
    outline: none;
}
.wrapper input:focus{
    border-bottom-color: #60296c;
}
.wrapper button{
    background: #da57ff;
    color:#fff;
    font-weight: 600;
    border-radius: 10px;
    border: 1px solid #da57ff;
    padding: 10px 15px;
    margin-left: 20px;
    cursor: pointer;
    transition:transform 500ms ease;
}
.wrapper button:hover{
    transform: scale(1.1) translateY(-2px);
}
</style>
