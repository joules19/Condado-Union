<template>
  <div
    class="
      relative
      flex flex-col
      min-w-0
      break-words
      w-full
      mb-6
      shadow-lg
      rounded-lg
      bg-blueGray-100
      border-0
    "
  >
    <div class="rounded-t bg-white mb-0 px-6 py-6">
      <div class="text-center flex justify-between">
        <!-- <h6 class="text-blueGray-700 text-xl font-semibold">My Account</h6> -->
        <h1 class="text-blueGray-400 text-xl font-semibold">My Account</h1>

        <base-button
          mode="solid sm-btn with-gradient dark-text"
          @click="updateAccount"
        >
          {{ updateText }}</base-button
        >
      </div>
    </div>
    <div class="flex-auto px-4 lg:px-10 py-10 mt-2 pt-0">
      <transition name="alert">
        <div class="flex flex-wrap justify-end" v-show="alertShow">
          <the-alert
            @click="close"
            :alertMessage="alertMessage"
            :alertMode="alertMode"
          ></the-alert>
        </div>
      </transition>
      <form>
        <h6 class="text-blueGray-400 text-sm mt-3 mb-6 font-bold uppercase">
          Account Information
        </h6>
        <div class="flex flex-wrap">
          <div class="w-full lg:w-6/12 px-4">
            <div class="relative w-full mb-3">
              <label class="block text-blueGray-600 text-s font-normal mb-2">
                Account Id
              </label>
              <input
                type="text"
                class="
                  border-0
                  px-3
                  py-3
                  placeholder-blueGray-300
                  text-blueGray-600
                  bg-white
                  rounded
                  text-sm
                  shadow
                  focus:outline-none focus:ring
                  w-full
                  ease-linear
                  transition-all
                  duration-150
                "
                :value="accountId()"
                disabled
              />
            </div>
          </div>
          <div class="w-full lg:w-6/12 px-4">
            <div class="relative w-full mb-3">
              <label class="block text-blueGray-600 text-s font-normal mb-2">
                Email address
              </label>
              <input
                type="email"
                class="
                  border-0
                  px-3
                  py-3
                  placeholder-blueGray-300
                  text-blueGray-600
                  bg-white
                  rounded
                  text-sm
                  shadow
                  focus:outline-none focus:ring
                  w-full
                  ease-linear
                  transition-all
                  duration-150
                "
                placeholder="Email"
                :value="userEmail()"
                disabled
              />
            </div>
          </div>
          <div class="w-full lg:w-6/12 px-4">
            <div class="relative w-full mb-3">
              <label class="block text-blueGray-600 text-s font-normal mb-2">
                First Name
              </label>
              <input
                type="text"
                class="
                  border-0
                  px-3
                  py-3
                  placeholder-blueGray-300
                  text-blueGray-600
                  bg-white
                  rounded
                  text-sm
                  shadow
                  focus:outline-none focus:ring
                  w-full
                  ease-linear
                  transition-all
                  duration-150
                "
                :value="firstName"
                placeholder="First Name"
                ref="firstName"
                :disabled="areInputsDisabled"
              />
            </div>
          </div>
          <div class="w-full lg:w-6/12 px-4">
            <div class="relative w-full mb-3">
              <label class="block text-blueGray-600 text-s font-normal mb-2">
                Last Name
              </label>
              <input
                type="text"
                class="
                  border-0
                  px-3
                  py-3
                  placeholder-blueGray-300
                  text-blueGray-600
                  bg-white
                  rounded
                  text-sm
                  shadow
                  focus:outline-none focus:ring
                  w-full
                  ease-linear
                  transition-all
                  duration-150
                "
                placeholder="Last Name"
                :value="lastName"
                ref="lastName"
                :disabled="areInputsDisabled"
              />
            </div>
          </div>
          <div class="w-full lg:w-6/12 px-4">
            <div class="relative w-full mb-3">
              <label class="block text-blueGray-600 text-s font-normal mb-2">
                D.O.B
              </label>
              <input
                type="date"
                class="
                  border-0
                  px-3
                  py-3
                  placeholder-blueGray-300
                  text-blueGray-600
                  bg-white
                  rounded
                  text-sm
                  shadow
                  focus:outline-none focus:ring
                  w-full
                  ease-linear
                  transition-all
                  duration-150
                "
                placeholder="Birth Date"
                :value="dob"
                ref="dob"
                :disabled="areInputsDisabled"
              />
            </div>
          </div>

          <!-- <div class="w-full lg:w-6/12 px-4">
            <div class="relative w-full mb-3">
              <label
                class="block text-blueGray-600 text-s font-normal mb-2"
                
              >
                Change Display Picture
              </label>
              <input
                @change="onFileSelected"
                type="file"
                accept="image/*"
                class="
                  border-0
                  px-3
                  py-3
                  placeholder-blueGray-300
                  text-blueGray-600
                  bg-white
                  rounded
                  text-sm
                  shadow
                  focus:outline-none focus:ring
                  w-full
                  ease-linear
                  transition-all
                  duration-150
                "
              />
            </div>
            <img :src="imageUrl" height="150">
          </div> -->
          <p
            class="
              text-xs
              px-4
              text-center
              mt-2
              font-normal
              leading-relaxed
              text-blueGray-400
            "
          >
            For security reasons, we have left the account ID and E-mail fields
            un-editable.
          </p>
        </div>

        <hr class="mt-6 border-b-1 border-blueGray-300" />

        <h6 class="text-blueGray-400 text-sm mt-3 mb-6 font-bold uppercase">
          Contact Information
        </h6>
        <div class="flex flex-wrap">
          <div class="w-full lg:w-12/12 px-4">
            <div class="relative w-full mb-3">
              <label class="block text-blueGray-600 text-s font-normal mb-2">
                Home Address
              </label>
              <input
                type="text"
                class="
                  border-0
                  px-3
                  py-3
                  placeholder-blueGray-300
                  text-blueGray-600
                  bg-white
                  rounded
                  text-sm
                  shadow
                  focus:outline-none focus:ring
                  w-full
                  ease-linear
                  transition-all
                  duration-150
                "
                placeholder="Home Address"
                :value="address"
                ref="address"
                :disabled="areInputsDisabled"
              />
            </div>
          </div>
          <div class="w-full lg:w-4/12 px-4">
            <div class="relative w-full mb-3">
              <label class="block text-blueGray-600 text-s font-normal mb-2">
                City
              </label>
              <input
                type="text"
                class="
                  border-0
                  px-3
                  py-3
                  placeholder-blueGray-300
                  text-blueGray-600
                  bg-white
                  rounded
                  text-sm
                  shadow
                  focus:outline-none focus:ring
                  w-full
                  ease-linear
                  transition-all
                  duration-150
                "
                placeholder="City"
                :value="city"
                ref="city"
                :disabled="areInputsDisabled"
              />
            </div>
          </div>
          <div class="w-full lg:w-4/12 px-4">
            <div class="relative w-full mb-3">
              <label class="block text-blueGray-600 text-s font-normal mb-2">
                County
              </label>
              <input
                type="text"
                class="
                  border-0
                  px-3
                  py-3
                  placeholder-blueGray-300
                  text-blueGray-600
                  bg-white
                  rounded
                  text-sm
                  shadow
                  focus:outline-none focus:ring
                  w-full
                  ease-linear
                  transition-all
                  duration-150
                "
                placeholder="County"
                :value="county"
                ref="county"
                :disabled="areInputsDisabled"
              />
            </div>
          </div>
          <div class="w-full lg:w-4/12 px-4">
            <div class="relative w-full mb-3">
              <label class="block text-blueGray-600 text-s font-normal mb-2">
                Postal Code
              </label>
              <input
                type="text"
                class="
                  border-0
                  px-3
                  py-3
                  placeholder-blueGray-300
                  text-blueGray-600
                  bg-white
                  rounded
                  text-sm
                  shadow
                  focus:outline-none focus:ring
                  w-full
                  ease-linear
                  transition-all
                  duration-150
                "
                placeholder="Postal Code"
                :value="postalCode"
                ref="postalCode"
                :disabled="areInputsDisabled"
              />
            </div>
          </div>
        </div>

        <hr class="mt-6 border-b-1 border-blueGray-300" />

        <h6 class="text-blueGray-400 text-sm mt-3 mb-6 font-bold uppercase">
          Business Information
        </h6>
        <div class="flex flex-wrap">
          <div class="w-full lg:w-12/12 px-4">
            <div class="relative w-full mb-3">
              <label class="block text-blueGray-600 text-s font-normal mb-2">
                Business Address
              </label>
              <input
                type="text"
                class="
                  border-0
                  px-3
                  py-3
                  placeholder-blueGray-300
                  text-blueGray-600
                  bg-white
                  rounded
                  text-sm
                  shadow
                  focus:outline-none focus:ring
                  w-full
                  ease-linear
                  transition-all
                  duration-150
                "
                placeholder="Business Address"
                :value="businessAddress"
                ref="businessAddress"
                :disabled="areInputsDisabled"
              />
            </div>
          </div>
          <div class="w-full lg:w-4/12 px-4">
            <div class="relative w-full mb-3">
              <label class="block text-blueGray-600 text-s font-normal mb-2">
                Business Name
              </label>
              <input
                type="email"
                class="
                  border-0
                  px-3
                  py-3
                  placeholder-blueGray-300
                  text-blueGray-600
                  bg-white
                  rounded
                  text-sm
                  shadow
                  focus:outline-none focus:ring
                  w-full
                  ease-linear
                  transition-all
                  duration-150
                "
                placeholder="Business Name"
                :value="businessName"
                ref="businessName"
                :disabled="areInputsDisabled"
              />
            </div>
          </div>
          <div class="w-full lg:w-4/12 px-4">
            <div class="relative w-full mb-3">
              <label class="block text-blueGray-600 text-s font-normal mb-2">
                Business City
              </label>
              <input
                type="text"
                class="
                  border-0
                  px-3
                  py-3
                  placeholder-blueGray-300
                  text-blueGray-600
                  bg-white
                  rounded
                  text-sm
                  shadow
                  focus:outline-none focus:ring
                  w-full
                  ease-linear
                  transition-all
                  duration-150
                "
                placeholder="Business City"
                :value="businessCity"
                ref="businessCity"
                :disabled="areInputsDisabled"
              />
            </div>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  props: ["loading", "alertShow", "alertMessage", "alertMode"],
  emits: ["save-data", "closeAlert"],
  data() {
    return {
      imageUrl: "",
      selectedFile: null,
    };
  },
  computed: {
    firstName() {
      return this.$store.getters["account/firstName"];
    },
    lastName() {
      return this.$store.getters["account/lastName"];
    },
    dob() {
      return this.$store.getters["account/dob"];
    },
    address() {
      return this.$store.getters["account/address"];
    },
    city() {
      return this.$store.getters["account/city"];
    },
    county() {
      return this.$store.getters["account/county"];
    },
    postalCode() {
      return this.$store.getters["account/postalCode"];
    },
    businessName() {
      return this.$store.getters["account/businessName"];
    },
    businessAddress() {
      return this.$store.getters["account/businessAddress"];
    },
    businessCity() {
      return this.$store.getters["account/businessCity"];
    },
    isUpdating() {
      return this.$store.getters["account/isUpdating"];
    },
    areInputsDisabled() {
      return this.$store.getters["account/areInputsDisabled"];
    },

    updateText() {
      if (this.isUpdating) {
        return "Please Wait...";
      } else if (this.areInputsDisabled) {
        return "Edit";
      } else if (!this.areInputsDisabled) {
        return "Update";
      }
      return this.updateText;
    },
  },
  methods: {
    onFileSelected(event) {
      const file = event.target.files[0];
      let fileName = file.name;
      if (fileName.lastIndexOf(".") <= 0) {
        return alert("Please add a valid file");
      }
      const fileReader = new FileReader();
      fileReader.addEventListener("load", () => {
        this.imageUrl = fileReader.result;
      });
      fileReader.readAsDataURL(file);
      this.selectedFile = file;
    },
    // setInputsStatus() {
    //   this.areInputsDisabled = true;
    // },
    updateAccount() {
      if (this.areInputsDisabled === true) {
        this.$store.dispatch("account/setInputsStatus", {
          status: false,
        });

        return;
      }

      const accountData = {
        accountId: this.$store.getters["account/accountId"],
        userEmail: this.$store.getters["account/userEmail"],
        firstName: this.$refs.firstName.value,
        lastName: this.$refs.lastName.value,
        dob: this.$refs.dob.value,
        address: this.$refs.address.value,
        city: this.$refs.city.value,
        county: this.$refs.county.value,
        postalCode: this.$refs.postalCode.value,
        businessName: this.$refs.businessName.value,
        businessAddress: this.$refs.businessAddress.value,
        businessCity: this.$refs.businessCity.value,
        imageUrl: this.$store.getters["account/imageUrl"],
      };

      this.$emit("save-data", accountData);

      // areInputsDisabled is set back to true in ./view/CardAccount
      // upon successfull account update
    },
    accountId() {
      const accountIdA = localStorage.getItem("accountId");
      const accountIdB = this.$store.getters["account/accountId"];
      if (!accountIdB) {
        return accountIdA;
      } else {
        return accountIdB;
      }
    },
    userEmail() {
      const userEmailA = localStorage.getItem("userEmail");
      const userEmailB = this.$store.getters["account/userEmail"];
      if (!userEmailB) {
        return userEmailA;
      } else {
        return userEmailB;
      }
    },
    close() {
      this.$emit("closeAlert");
    },
  },
  created() {},
};
</script>
