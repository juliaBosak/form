<!--suppress ES6ShorthandObjectProperty -->
<template>
	<section class="form-popup">
		<div class="main-nav">
			<div class="main-nav__content">
				<button class="circle-button up-button" @click="change(0)"></button>
				<ul class="dots">
					<li class="dot"></li>
					<li class="dot "></li>
					<li class="dot "></li>
					<li class="dot active"></li>
				</ul>
				<button class="circle-button down-button"></button>
				<div class="rounded-rectangle-1 blue-rounded-rectangle"></div>
				<div class="rounded-rectangle-2 gray-rounded-rectangle"></div>
				<div class="rounded-rectangle-3 blue-rounded-rectangle"></div>
				<div class="rounded-rectangle-4 gray-rounded-rectangle"></div>

			</div>
		</div>
		<div class="form-popup__content">
			<h3 class="form-popup__title title-h3">Next Details</h3>
			<form action="" class="main-form" @submit.prevent="">
				<div class="main-form__fields">
					<div class="main-form__column">
						<label class="main-form__input-wrap field__wrap">
							<input
									class="field basic-field"
									placeholder=" "
									v-model="firstName"
									id="firstName"
									:class="{ error: isFirstNameError, success: isFirstNameValid }"
									@blur="isFirstNameTouched = true"
									@focus="isFirstNameTouched = false, reset = false">
							<span class="field__label">First Name</span>
							<span class="field__border"></span>
							<i class="zmdi zmdi-check success-icon"></i>
						</label>
						<label class="main-form__input-wrap field__wrap">
							<input
									class="field basic-field"
									placeholder=" "
									v-model="email"
									id="email"
									:class="{ error: isEmailError, success: isEmailValid }"
									@blur="isEmailTouched = true"
									@focus="isEmailTouched = false,  reset = false">
							<span class="field__label">Email ID</span>
							<span class="field__border"></span>
							<i class="zmdi zmdi-check success-icon"></i>
						</label>
						<label class="main-form__input-wrap field__wrap">
							<select
									v-model="countrySelected"
									class="field select-filed"
									:class="{selected: countrySelected,
									active: openCountrySelect,
									error: isCountryError}"
									@click="openCountrySelect = true"
									@blur="openCountrySelect = false, isCountryTouched = true"
									@focus="isCountryTouched = false,  reset = false">
								<option v-for="country in countries" v-bind:key="country.id" v-bind:value="country.id">
									{{country.name}}
								</option>
							</select>
							<span class="field__label">Country</span>
							<span class="field__border"></span>
							<i class="zmdi zmdi-chevron-down chevron-down-icon"></i>
						</label>
						<label class="main-form__input-wrap field__wrap">
							<input
									class="field basic-field"
									type="tel"
									placeholder=" "
									v-model="phoneNumber"
									id="phoneNumber"
									:class="{ error: isPhoneNumberError, success: isPhoneNumberValid }"
									@blur="isPhoneNumberTouched = true"
									@focus="isPhoneNumberTouched = false,  reset = false">
							<span class="field__label">Phone Number</span>
							<span class="field__border"></span>
							<i class="zmdi zmdi-check success-icon"></i>
						</label>
					</div>
					<div class="main-form__column">
						<label class="main-form__input-wrap field__wrap">
							<input
									class="field basic-field"
									placeholder=" "
									v-model="lastName"
									id="lastName"
									:class="{ error: isLastNameError, success: isLastNameValid }"
									@blur="isLastNameTouched = true"
									@focus="isLastNameTouched = false,  reset = false">
							<span class="field__label">Last Name</span>
							<span class="field__border"></span>
							<i class="zmdi zmdi-check success-icon"></i>
						</label>
						<label class="main-form__input-wrap field__wrap">
							<input
									class="field basic-field"
									placeholder=" "
									v-model="userID"
									id="userID"
									:class="{ error: isUserIDError, success: isUserIDValid }"
									@blur="isUserIDTouched = true"
									@focus="isUserIDTouched = false,  reset = false"
							>
							<span class="field__label">Your User ID</span>
							<span class="field__border"></span>
							<i class="zmdi zmdi-lock-outline lock-icon"></i>
							<i class="zmdi zmdi-check success-icon right20"></i>
						</label>
						<label class="main-form__input-wrap main-form__input-group">
							<label class="small-field__wrap field__wrap">
								<select
										v-model="stateSelected" class="field select-filed"
										:class="{selected: stateSelected, active: openStateSelect,
										error: isStateError}"
										@click="openStateSelect = true"
										@blur="openStateSelect = false, isStateTouched = true"
										@focus="isStateTouched = false,  reset = false">
									<option v-if="!countrySelected" disabled value="">Select country</option>
									<option v-for="state in purposeStates" v-bind:key="state.id" v-bind:value="state.id">
										{{state.name}}
									</option>
								</select>
								<span class="field__label">State</span>
								<span class="field__border"></span>
								<i class="zmdi zmdi-chevron-down chevron-down-icon"></i>
							</label>
							<label class="field__wrap small-field__wrap">
								<select
										id="countrySelect"
										v-model="citySelected"
										class="field select-filed"
										:class="{selected: citySelected, active: openCitySelect,
									error: isCityError}"
										@click="openCitySelect = true"
										@blur="openCitySelect = false, isCityTouched = true"
										@focus="isCityTouched = false">
									<option v-if="!stateSelected" disabled value="">Select state</option>
									<option v-for="city in purposeCities" v-bind:key="city.id" v-bind:value="city.name">
										{{city.name}}
									</option>
								</select>
								<span class="field__label">City</span>
								<span class="field__border"></span>
								<i class="zmdi zmdi-chevron-down chevron-down-icon"></i>
							</label>
						</label>
						<label class="main-form__input-wrap field__wrap">
							<input
									class="field basic-field uppercase"
									placeholder=" "
									v-model="referenceCode"
									id="referenceCode"
									:class="{ error: isReferenceCodeError, success: isReferenceCodeValid }"
									@blur="isReferenceCodeTouched = true"
									@focus="isReferenceCodeTouched = false,  reset = false">
							<span class="field__label">Reference Code</span>
							<span class="field__border"></span>
							<i class="zmdi zmdi-check success-icon"></i>
						</label>
					</div>
				</div>
				<div class="main-form__buttons">
					<button class="blue-button" @click="setContinue(), checkForm()">Continue</button>
					<button class="reset-button" @click="resetForm()">Reset All</button>
				</div>
			</form>
		</div>
	</section>
</template>

<script>
	/* eslint-disable no-console */

	const emailCheckRegex = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
	const nameCheckRegex = /^[а-яёіїє]{2,50}$/iu;
	const phoneCheckRegex = /^\+380\d{9}$/;
	const userIDCheckRegex = /^[a-z_]{5,30}$/iu;
	const referenceCodeCheckRegex = /^[a-z0-9]{10}$/iu;

	export default {
		name: 'formNextDetails',
		props: {
			currentCountries: Array,
			currentStates: Array,
			currentCities: Array,

		},
		data() {
			return {
				firstName: null,
				lastName: null,
				email: null,
				phoneNumber: null,
				userID: null,
				referenceCode: null,
				countrySelected: null,
				stateSelected: null,
				citySelected: null,
				openCountrySelect: false,
				openStateSelect: false,
				openCitySelect: false,
				isFirstNameTouched: false,
				isLastNameTouched: false,
				isEmailTouched: false,
				isPhoneNumberTouched: false,
				isUserIDTouched: false,
				isReferenceCodeTouched: false,
				isCountryTouched: false,
				isStateTouched: false,
				isCityTouched: false,
				reset: false,
				countries: this.currentCountries,
				states: this.currentStates,
				cities: this.currentCities,
				purposeStates: null,
				purposeCities: null,
				gridData: null,
				nameForm: 'NextDetails',
				continue: false,
				validForm: false
			}
		},
		computed: {
			isFirstNameValid() {
				return this.firstName && nameCheckRegex.test(this.firstName);
			},
			isFirstNameError() {
				return !this.isFirstNameValid && this.isFirstNameTouched && !this.reset;
			},
			isEmailValid() {
				return this.email && emailCheckRegex.test(this.email);
			},
			isEmailError() {
				return !this.isEmailValid && this.isEmailTouched && !this.reset;
			},
			isPhoneNumberValid() {
				return this.phoneNumber && phoneCheckRegex.test(this.phoneNumber);
			},
			isPhoneNumberError() {
				return !this.isPhoneNumberValid && this.isPhoneNumberTouched && !this.reset;
			},
			isLastNameValid() {
				return this.lastName && nameCheckRegex.test(this.lastName);
			},
			isLastNameError() {
				return !this.isLastNameValid && this.isLastNameTouched && !this.reset;
			},
			isUserIDValid() {
				return this.userID && userIDCheckRegex.test(this.userID);
			},
			isUserIDError() {
				return !this.isUserIDValid && this.isUserIDTouched && !this.reset;
			},
			isReferenceCodeValid() {
				return this.referenceCode && referenceCodeCheckRegex.test(this.referenceCode);
			},
			isReferenceCodeError() {
				return !this.isReferenceCodeValid && this.isReferenceCodeTouched && !this.reset;
			},
			isCountryError() {
				return !this.countrySelected && this.isCountryTouched && !this.reset;
			},
			isStateError() {
				return !this.stateSelected && this.isStateTouched && !this.reset;
			},
			isCityError() {
				return !this.citySelected && this.isCityTouched && !this.reset;
			}
		},
		methods: {
			checkForm() {
				if (this.reset && this.continue) {
					this.setGridData();
					this.checkValid();
				} else {
					this.checkValid();
					if (this.validForm) {
						this.setGridData();
					}
				}
				this.reset = false;
				return this.validForm;
			},
			setContinue() {
				this.continue = true;
			},
			resetForm() {
				this.continue = false;
				const sureAnswer = confirm('Are you sure?');
				if (sureAnswer) {
					this.reset = true;
					this.firstName = null;
					this.isFirstNameTouched = false;
					this.email = null;
					this.isEmailTouched = false;
					this.phoneNumber = null;
					this.isPhoneNumberTouched = false;
					this.userID = null;
					this.isUserIDTouched = false;
					this.lastName = null;
					this.isLastNameTouched = false;
					this.referenceCode = null;
					this.isReferenceCodeTouched = false;
					this.countrySelected = null;
					this.isCountryTouched = false;
					this.stateSelected = null;
					this.isStateTouched = false;
					this.citySelected = null;
					this.isCityTouched = false;
				}
			},
			change(number) {
				if (this.checkForm()) {
					this.$emit('changePage', number);
				}
			},
			setGridData() {
				this.gridData = {
					FirstName: this.firstName,
					Email: this.email,
					CountryId: this.countrySelected,
					PhoneNumber: this.phoneNumber,
					LastName: this.lastName,
					UserID: this.userID,
					ReferenceCode: this.referenceCode,
					StateID: this.stateSelected,
					City: this.citySelected
				};
				localStorage.setItem(this.nameForm, JSON.stringify(this.gridData))
			},
			checkValid() {
				this.validForm = true;
				if (!this.isFirstNameValid) {
					this.isFirstNameTouched = true;
					this.validForm = false;
				}
				if (!this.isEmailValid) {
					this.isEmailTouched = true;
					this.validForm = false;
				}
				if (!this.countrySelected) {
					this.isCountryTouched = true;
					this.validForm = false;
				}
				if (!this.isPhoneNumberValid) {
					this.isPhoneNumberTouched = true;
					this.validForm = false;
				}
				if (!this.isLastNameValid) {
					this.isLastNameTouched = true;
					this.validForm = false;
				}
				if (!this.isUserIDValid) {
					this.isUserIDTouched = true;
					this.validForm = false;
				}
				if (!this.isReferenceCodeValid) {
					this.isReferenceCodeTouched = true;
					this.validForm = false;
				}
				if (!this.stateSelected) {
					this.isStateTouched = true;
					this.validForm = false;
				}
				if (!this.citySelected) {
					this.isCityTouched = true;
					this.validForm = false;
				}
			},
			updateValue() {
				this.firstName = this.gridData.FirstName;
				this.email = this.gridData.Email;
				this.countrySelected = this.gridData.CountryId;
				this.phoneNumber = this.gridData.PhoneNumber;
				this.lastName = this.gridData.LastName;
				this.userID = this.gridData.UserID;
				this.referenceCode = this.gridData.ReferenceCode;
				this.stateSelected = this.gridData.StateID;
				this.citySelected = this.gridData.City;
			}
		},
		watch: {
			countrySelected: {
				handler(value) {
					this.purposeStates = this.states.filter((state) => state.country_id === value);
					if (value) {
						this.stateSelected = null;
						this.citySelected = null;
					}
				}
			},
			stateSelected: {
				handler(value) {
					this.purposeCities = this.cities.filter((city) => city.state_id === value);
				}
			},
			gridData: {
				handler() {
					this.updateValue();
				}
			}
		},
		mounted() {
			if (localStorage.getItem(this.nameForm)) {
				this.gridData = JSON.parse(localStorage.getItem(this.nameForm));
				this.updateValue();
			}
		}
	}
</script>
