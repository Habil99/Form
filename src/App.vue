<template>
  <div class="container">
    <h3>Form Verileriyle Çalışmak</h3>
    <hr />
    <div class="row">
      <div class="col-md-6">
        <div class="panel panel-warning">
          <div class="panel-heading">
            <h4>Başvuru Formu</h4>
          </div>
          <div class="panel-body">
            <form>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label for="email">Kullanıcı Adı</label>
                    <input
                      v-model.lazy="userData.userName"
                      type="text"
                      id="username"
                      class="form-control"
                    />
                  </div>
                  <div class="form-group">
                    <label for="password">Şifre</label>
                    <input
                      v-model.lazy.number="userData.password"
                      type="password"
                      id="password"
                      class="form-control"
                    />
                  </div>
                  <div class="form-group">
                    <label for="age">Yaş</label>
                    <input
                      v-model="userData.age"
                      type="number"
                      id="age"
                      class="form-control"
                    />
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label for="message">Açıklama</label><br />
                  <textarea
                    v-model.lazy="userData.explanation"
                    id="message"
                    rows="3"
                    class="form-control"
                  ></textarea>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12">
                  <div class="form-group">
                    <label>
                      <input
                        v-model="userData.interests"
                        type="checkbox"
                        value="Yazılım"
                      />
                      Yazılım
                    </label>
                    <label>
                      <input
                        v-model="userData.interests"
                        type="checkbox"
                        value="Donanım"
                      />
                      Donanım
                    </label>
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 form-group">
                  <label>
                    <input
                      v-model="userData.gender"
                      type="radio"
                      value="Erkek"
                    />
                    Erkek
                  </label>
                  <label>
                    <input
                      v-model="userData.gender"
                      type="radio"
                      value="Kadın"
                    />
                    Kadın
                  </label>
                </div>
              </div>
              <div class="row">
                <div class="col-md-12 from-group">
                  <label>Şehir</label>
                  <select v-model="userData.selectedCity" class="form-control">
                    <option
                      :selected="city == 'Lənkəran'"
                      v-for="city in userData.cities"
                    >
                      {{ city }}
                    </option>
                  </select>
                </div>
              </div>
              <hr />
              <div class="row">
                <div class="col-md-12">
                  <button class="btn btn-primary" @click.prevent="submit">Gönder!</button>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
      <div class="col-md-6" v-if="isSubmitted">
        <div class="panel panel-info">
          <div class="panel-heading">
            <h4>Form Verileri</h4>
          </div>
          <div class="panel-body">
            <p>Kullanıcı Adı: {{ userData.userName }}</p>
            <p>Şifre: {{ userData.password }}</p>
            <p>Yaş: {{ userData.age }}</p>
            <p style="white-space: pre;">
              Açıklama: {{ userData.explanation }}
            </p>
            <p><strong>İlgi Alanları :</strong></p>
            <ul>
              <li v-for="item in userData.interests">{{ item }}</li>
            </ul>
            <p>Cinsiyet: {{ userData.gender }}</p>
            <p>Şehir: {{ userData.selectedCity }} </p>
            <p>Toggle:</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userData: {
        userName: "",
        password: "",
        age: null,
        explanation: "",
        interests: [],
        gender: "",
        cities: [
          "Lənkəran",
          "Astara",
          "Bakı",
          "Abşeron",
          "Qazax",
          "Bərdə",
          "Quba"
        ],
        selectedCity: '',
      },
      isSubmitted: false,
    };
  },
  methods: {
    submit() {
      this.isSubmitted = true
    }
  },
};
</script>

<style>
li {
  list-style: none;
  background-color: red;
  color: white;
  padding: 2px 3px;
  margin-left: 3px;
  display: inline-block;
}
</style>
