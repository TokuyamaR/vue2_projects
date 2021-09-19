<template>
    <div class="container">
        <div class="row justify-content-center">
            <div class="col-md-8">
                <div class="card">
                    <div v-show="checkedNames.length > 0" class="card-header">
                        Example Component
                    </div>

                    <div v-on:click="plusOne" class="card-body">
                        {{ count }}
                        <input type="text" v-model="text" />
                        <input type="date" v-model="date" />
                        <input type="email" v-model="email" />
                        <input type="tel" v-model="tel" />
                        <textarea
                            v-model="textarea"
                            name="textarea"
                            id=""
                            cols="30"
                            rows="10"
                        ></textarea>
                        <input
                            v-model="checkedNames"
                            type="checkbox"
                            value="checkbox01"
                        />
                        <input
                            v-model="checkedNames"
                            type="checkbox"
                            value="checkbox02"
                        />
                        <select v-model="selectedCharacter" multiple>
                            <option disabled value=""
                                >花嫁を選択してください</option
                            >
                            <option>中野一花</option>
                            <option>中野二乃</option>
                            <option>中野三玖</option>
                            <option>中野四葉</option>
                            <option>中野五月</option>
                        </select>
                        <p>{{ text }}</p>
                        <p>{{ date }}</p>
                        <p>{{ email }}</p>
                        <p>{{ tel }}</p>
                        <p>{{ textarea }}</p>
                        <p>{{ checkedNames }}</p>
                        <p>選ばれたのは:{{ selectedCharacter }}</p>
                    </div>
                    <h2>奇数</h2>
                    <ul v-for="num of odd">
                        <li>{{ num }}</li>
                    </ul>
                    <h2>偶数</h2>
                    <ul v-for="num of even">
                        <li>{{ num }}</li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "ExampleComponent",
    data() {
        return {
            count: 0,
            text: "",
            date: "1991-10-07",
            email: "",
            tel: "",
            textarea: "",
            checkedNames: [],
            selectedCharacter: [],
            numArray: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
        };
    },
    methods: {
        plusOne() {
            this.count++;
        }
    },
    computed: {
        odd() {
            return this.numArray.filter(num => {
                return num % 2 !== 0;
            });
        },
        even() {
            return this.numArray.filter(num => {
                return num % 2 === 0;
            });
        }
    }
};
</script>
