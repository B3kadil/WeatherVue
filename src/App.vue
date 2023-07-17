<script>
import axios from "axios";

export default {
    data: () => ({
        Title: 'Погодное приложение',
        city: '',
        error: '',
        info: null
    }),
    methods: {
        getWeather() {
            if (this.city.trim().length < 2) {
                this.error = 'Нужно название более одного символа'
                return false
            }
            this.error = ''
            axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=735bb03774533f37710a31f65f3dda66`)
                .then(res => (this.info = res.data))
        }
    },
    computed: {
        cityName() {
            return '"' + this.city + '"'
        },
        showTemp() {
            return "Температура: " + this.info.main.temp + '°C'
        },
        showFeelsLike() {
            return "Ощущается как: " + this.info.main.feels_like + '°C'
        },
        showMinTemp() {
            return "Минимальная температура: " + this.info.main.temp_min + '°C'
        },
        showMaxTemp() {
            return "Максимальная температура: " + this.info.main.temp_max + '°C'
        }
    }
}
</script>

<template>
    <div class="wrapper">
        <h1>{{ Title }}</h1>
        <p>Узнать погоду в {{ city == "" ? "вашем городе" : cityName }}</p>
        <input
                v-model="city"
                @keydown.enter="getWeather()"
                type="text" name="" id="" placeholder="Введите название города">
        <button
                v-show="city!==''"
                @click="getWeather()"
        >Получить погоду
        </button>
        <p class="error">{{ error }}</p>

        <div v-if="info!=null">
            <p>{{ showTemp }}</p>
            <p>{{ showFeelsLike }}</p>
            <p>{{ showMinTemp }}</p>
            <p>{{ showMaxTemp }}</p>
        </div>
    </div>
</template>

<style scoped>
.error {
    color: #d03939;
    font-size: 14px;
}

.wrapper {
    width: 900px;
    height: 500px;
    border-radius: 50px;
    background: linear-gradient(135deg, #0044da, #9400b4);
    padding: 20px;
    color: #fff;
    text-align: center;
}

.wrapper h1 {
    margin-top: 50px;
}

.wrapper p {
    margin-top: 20px;
}

.wrapper input {
    margin-top: 30px;
    background: transparent;
    border: 0;
    border-bottom: 2px solid #110813;
    color: #ffffff;
    font-size: 14px;
    padding: 5px 8px;
    outline: none;
}

.wrapper input:focus {
    border-bottom-color: #60296c;
}

.wrapper button {
    background: #da57ff;
    color: #fff;
    font-weight: 600;
    border-radius: 10px;
    border: 1px solid #da57ff;
    padding: 10px 15px;
    margin-left: 20px;
    cursor: pointer;
    transition: transform 500ms ease;
}

.wrapper button:hover {
    transform: scale(1.1) translateY(-2px);
}
</style>
