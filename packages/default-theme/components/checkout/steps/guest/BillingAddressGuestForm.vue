<template>
  <div>
    <SfCheckbox
      v-model="differentThanShipping"
      label="Use different address for billing"
      name="copyShippingAddress"
      class="sw-form__checkbox"
      data-cy="different-address-for-billing"
    />
    <div v-if="differentThanShipping" class="sw-form" data-cy="form">
      <div class="inputs-group">
        <SwInput
          v-model="firstName"
          :valid="!validations.firstName.$error"
          error-message="This field is required"
          label="First name"
          data-cy="first-name"
          name="firstName"
          class="sw-form__input"
          required
        />
        <SwInput
          v-model="lastName"
          :valid="!validations.lastName.$error"
          error-message="This field is required"
          label="Last name"
          data-cy="last-name"
          name="lastName"
          class="sw-form__input"
          required
        />
        <SwInput
          v-model="street"
          :valid="!validations.street.$error"
          error-message="This field is required"
          label="Street name"
          data-cy="street-name"
          name="street"
          class="sw-form__input"
          required
        />
      </div>
      <div class="inputs-group">
        <SwInput
          v-model="apartment"
          :valid="!validations.apartment.$error"
          error-message="This field is required"
          label="House/Apartment number"
          data-cy="apartment"
          name="apartment"
          class="sw-form__input"
          required
        />
        <SwInput
          v-model="city"
          :valid="!validations.city.$error"
          error-message="This field is required"
          label="City"
          data-cy="city"
          name="city"
          class="sw-form__input"
          required
        />
        <SwInput
          v-model="state"
          :valid="!validations.state.$error"
          error-message="This field is required"
          label="State/Province"
          data-cy="state"
          name="state"
          class="sw-form__input"
          required
        />
      </div>
      <div class="inputs-group">
        <SwInput
          v-model="zipcode"
          :valid="!validations.zipcode.$error"
          error-message="This field is required"
          label="Zip-code"
          data-cy="zipcode"
          name="zipcode"
          class="sw-form__input"
          required
        />
        <SfSelect
          v-if="getCountries.length"
          v-model="countryId"
          :valid="!validations.countryId.$error"
          error-message="This field is required"
          label="Country"
          data-cy="country"
          class="sw-form__select sf-select--underlined"
          required
        >
          <SfSelectOption
            v-for="countryOption in getCountries"
            :key="countryOption.id"
            :value="countryOption.id"
          >
            {{ countryOption.name }}
          </SfSelectOption>
        </SfSelect>
        <SwInput
          v-model="phoneNumber"
          :valid="!validations.phoneNumber.$error"
          error-message="This field is required"
          label="Phone number"
          data-cy="phone"
          name="phone"
          class="sw-form__input"
          required
        />
      </div>
    </div>
  </div>
</template>
<script>
import { SfSelect, SfCheckbox } from "@storefront-ui/vue"
import { validationMixin } from "vuelidate"
import {
  usePaymentStep,
  usePaymentStepValidationRules,
} from "@shopware-pwa/default-theme/logic/checkout/usePaymentStep"
import { useCountries } from "@shopware-pwa/composables"
import SwInput from "@shopware-pwa/default-theme/components/atoms/SwInput"

export default {
  name: "BillingAddressGuestForm",
  components: {
    SwInput,
    SfSelect,
    SfCheckbox,
  },
  mixins: [validationMixin],
  setup(props, { root }) {
    const {
      validations,
      setValidations,
      firstName,
      lastName,
      street,
      apartment,
      city,
      state,
      zipcode,
      countryId,
      phoneNumber,
      differentThanShipping,
    } = usePaymentStep(root)

    const { getCountries } = useCountries(root)

    return {
      validations,
      setValidations,
      firstName,
      lastName,
      street,
      apartment,
      city,
      state,
      zipcode,
      countryId,
      phoneNumber,
      differentThanShipping,
      getCountries,
    }
  },
  watch: {
    $v: {
      immediate: true,
      handler() {
        this.setValidations(this.$v)
      },
    },
  },
  validations: {
    ...usePaymentStepValidationRules,
  },
}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/forms";
</style>
