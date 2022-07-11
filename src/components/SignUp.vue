<template>
    <h1>Sign Up Form</h1>

    <div class="formClass">
        <form @submit.prevent="submit">
            <label for="">Email</label>
            <input type="email" required v-model="email" />
            <label for="">Password</label>
            <input type="password" required v-model="password" />
            <p v-if="errorMsg" class="error">{{ errorMsg }}</p>

            <label for="">Roles: </label>
            <select v-model="role">
                <option value="developer">Web Developer</option>
                <option value="designer">Web Designer</option>
            </select>
            <div>
                <label for="">Skills</label>
                <input type="text" @keyup.shift="addSkill" v-model="skill" required />
            </div>
            <div class="skillBox" v-for="skill in skills" :key="skill">
                <p>
                    <span class="delItem" @click="deleteItem(skill)"
                        >&#10006;</span
                    >
                    - {{ skill }}
                </p>
            </div>
            <div class="checkbox">
                <input type="checkbox" v-model="accept" />
                <label>Accept Terms and conditions</label>
            </div>
            <div class="submitBtn">
                <button type="submit" class="submit">Create an account</button>
            </div>
            <!-- <label for="">Choose your favorites language</label>
            <div>
                <input type="checkbox" value="style_structure" v-model="names"  />
                <label>HTML, CSS, JavaScript</label>
            </div>
            <div>
                <input type="checkbox" value="frontend_framwork" v-model="names" />
                <label>VueJS, React, Javascript</label>
            </div>
            <div>
                <input type="checkbox" value="backend_framwork" v-model="names" />
                <label>PHP, Python, Laravel</label>
            </div> -->
        </form>
    </div>
    <!-- <p>email - {{ email }}</p>
    <p>password - {{ password }}</p>
    <p>role - {{ role }}</p>
    <p>accept - {{ accept }}</p> -->

    <!-- <p>names - {{names}}</p> -->
</template>

<script>
export default {
    data() {
        return {
            email: "coder.anaconda@gmail.com",
            password: "",
            role: "developer",
            accept: false,
            names: [],
            skills: [],
            skill: "",
            errorMsg: "",
        };
    },
    methods: {
        addSkill(e) {
            // console.log(e.key)
            if (e.key === " ") {
                this.skills.push(this.skill);
                this.skill = "";
            }
        },
        deleteItem(skill) {
            this.skills = this.skills.filter((loopSkill) => {
                return loopSkill != skill;
            });
        },
        submit() {
            if (this.password.length < 8) {
                this.errorMsg = "- password must be at least 8 charaters";
            }
        },
    },
};
</script>
	
<style>
h1 {
    color: white;
    text-shadow: 0 0 2px black;
}
.formClass {
    background-color: white;
    max-width: 420px;
    margin: 30px auto;
    padding: 40px;
    text-align: left;
    border-radius: 10px;
    box-shadow: 0 0 5px rgb(168, 168, 168);
}
label {
    color: #aaa;
    margin: 25px 0 15px;
    display: inline-block;
    text-transform: uppercase;
    letter-spacing: 2px;
    font-size: 0.6em;
    font-weight: bold;
}
input,
select {
    display: block;
    width: 100%;
    border: none;
    border-bottom: 1px solid #ddd;
    padding: 10px 4px;
    box-sizing: border-box;
    color: #555;
}
input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    position: relative;
    top: 2px;
    margin: 0 10px 0 0;
}
.delItem {
    cursor: pointer;
    color: red;
}
.skillBox {
    background-color: #ddd;
    display: inline-block;
    width: auto;
    height: auto;
    font-size: 14px;
    margin: 15px 5px 5px 0;
    padding: 0px 15px 0px 15px;
    text-align: center;
    border: none;
    border-radius: 5px;
    color: rgb(131, 131, 131);
}
.submit {
    background-color: rgb(0, 153, 255);
    color: white;
    padding: 10px 15px;
    border: none;
    text-align: center;
    border-radius: 10px;
}
.submitBtn {
    text-align: center;
    margin-top: 15px;
}
.error {
    color: crimson;
    font-size: 12px;
}
</style>