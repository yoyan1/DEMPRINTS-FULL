<template>
  <div class="q-pa-md q-gutter-sm">
    <q-skeleton width="300px" height="200px" @click="prompt = true"/>

    <q-dialog v-model="prompt" >
      <q-card class="no-shadow" >
        <q-card-section>
          <div class="text-h6">Create User</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          <q-stepper
            v-model="step"
            ref="stepper"
            vertical
            alternative-labels
            color="primary"
            animated
          >
            <q-step
              :name="1"
              title="Credentials"
              icon="settings"
              :done="step > 1"
            >
              <div class="flex flex-row gap-5">
                <q-input filled dense v-model="email" type="email" prefix="Email:" >
                  <template v-slot:prepend>
                    <q-icon name="mail" />
                  </template>
                </q-input>
                <q-input
                  outlined
                  color="primary"
                  type="password"
                  v-model="credentials.password"
                  label="password"
                  lazy-rules
                  :rules="[ val => val && val.length > 0 || 'Please type something']"
                  dense
                />
              </div>
            </q-step>

            <q-step
              :name="2"
              title="Personal Information"
              icon="create_new_folder"
              :done="step > 2"
            >
              <div class="q-py-md">
                <span class="py-4">NAME</span>
                <div class="flex justify-between gap-5">
                  <q-input
                    outlined
                    color="primary"
                    v-model="credentials.personal_information.firstname"
                    label="First name"
                    dense

                  />
                  <q-input
                    outlined
                    color="primary"
                    v-model="credentials.personal_information.middlename"
                    label="Middle name (optional)"
                    dense

                  />
                  <q-input
                    outlined
                    color="primary"
                    v-model="credentials.personal_information.lastname"
                    label="Last name"
                    dense

                  />
                </div>
              </div>
              <q-separator/>
              <div class="q-py-md">
                <div class="flex justify-between gap-5">
                  <q-select label="gender" dense outlined v-model="credentials.personal_information.gender" :options="['male', 'female']"/>
                </div>
              </div>
              <q-separator/>
              <div class="q-py-md">
                <span>CONTACT INFORMATION</span>
                <div class="flex justify-between gap-5">
                  <q-input
                    outlined
                    color="primary"
                    v-model="credentials.personal_information.address"
                    label="Address"
                    dense

                  />
                  <q-input
                    outlined
                    type="number"
                    color="primary"
                    v-model="credentials.personal_information.contact_number"
                    label="Contact no."
                    dense

                  />
                  <q-input
                    v-model="credentials.personal_information.email"
                    label="Email"
                    outlined
                    dense

                  />
                </div>
              </div>
              <q-separator/>
              <div class="q-py-md">
                <span>CONTACT PERSON</span>
                <div class="flex justify-between gap-5">
                  <q-input
                    outlined
                    color="primary"
                    v-model="credentials.personal_information.contact_person.name"
                    label="Name"
                    dense

                  />
                  <q-input
                    outlined
                    color="primary"
                    v-model="credentials.personal_information.contact_person.address"
                    label="Address"
                    dense

                  />
                  <q-input
                    outlined
                    type="number"
                    color="primary"
                    v-model="credentials.personal_information.contact_person.contact_number"
                    label="Contact no."
                    dense

                  />
                  <q-input
                    outlined
                    color="primary"
                    v-model="credentials.personal_information.contact_person.relationship"
                    label="Relationship"
                    dense

                  />
                </div>
              </div>
              <q-separator/>
              <div class="q-py-md">
                <span>MANDATORY BENEFIT CONTRIBUTION DETAILS</span>
                <div class="flex justify-between gap-5">
                  <q-input
                    filled
                    v-model="credentials.personal_information.ss_no"
                    label="SS #"
                    mask="#### #### #### ####"
                    fill-mask="#"
                    dense
                  />
                  <q-input
                    filled
                    v-model="credentials.personal_information.pagibig_no"
                    label="PAGIBIG #"
                    mask="#### #### #### ####"
                    fill-mask="#"
                    dense
                  />
                  <q-input
                    fiiled
                    v-model="credentials.personal_information.philhealth"
                    label="PHILHEALTH #"
                    mask="#### #### #### ####"
                    fill-mask="#"
                    dense
                  />
                </div>
              </div>
            </q-step>

            <q-step
              :name="3"
              title="Employment Details"
              icon="add_comment"
              :done="step > 3"
            >
              <div class="q-py-md">
                <span>JOB TITLE</span>
                <div class="flex  gap-3">
                  <q-select filled v-model="model" :options="jobOptions" label="Job Title" style="width:205px"/>
                  <q-select filled v-model="department" :options="depOptions" label="Department" style="width:205px"/>
                  <q-input filled v-model="credentials.personal_information.birth_date" mask="date" :rules="['date']" style="width:205px">
                    <template v-slot:append>
                      <q-icon name="event" class="cursor-pointer">
                        <q-popup-proxy cover transition-show="scale" transition-hide="scale">
                          <q-date v-model="date">
                            <div class="row items-center justify-end">
                              <q-btn v-close-popup label="Close" color="primary" flat />
                            </div>
                          </q-date>
                        </q-popup-proxy>
                      </q-icon>
                    </template>
                  </q-input>
                </div>
              </div>
            </q-step>

            <q-step
              :name="4"
              title="Compensation and Benefits"
              icon="add_comment"
              :done="step > 4"
            >
              <div class="q-py-md">
                <span class="py-4">SALARY DETAILS</span>
                <div class="flex justify-between gap-5">
                  <q-input
                    outlined
                    color="primary"
                    v-model="credentials.email"
                    label="First name"
                    dense

                  />
                  <q-input
                    outlined
                    color="primary"
                    v-model="credentials.email"
                    label="Middle name (optional)"
                    dense

                  />
                  <q-input
                    outlined
                    color="primary"
                    v-model="credentials.email"
                    label="Last name"
                    dense

                  />
                </div>
              </div>
            </q-step>
            <q-step
              :name="5"
              title="Legal Compliance and Audit"
              icon="add_comment"
              :done="step > 5"
            >
              Try out different ad text to see what brings in the most customers, and learn how to
              enhance your ads using features like ad extensions. If you run into any problems with
              your ads, find out how to tell if they're running and how to resolve approval issues.
            </q-step>
            <q-step
              :name="6"
              title="Performance Record"
              icon="add_comment"
            >
              Try out different ad text to see what brings in the most customers, and learn how to
              enhance your ads using features like ad extensions. If you run into any problems with
              your ads, find out how to tell if they're running and how to resolve approval issues.
            </q-step>
            <template v-slot:navigation>
              <q-stepper-navigation>
                <q-btn @click="$refs.stepper.next()" color="primary" :label="step === 6 ? 'Finish' : 'Continue'" />
                <q-btn v-if="step > 1" flat color="primary" @click="$refs.stepper.previous()" label="Back" class="q-ml-sm" />
              </q-stepper-navigation>
            </template>
          </q-stepper>
        </q-card-section>
      </q-card>
    </q-dialog>
  </div>
</template>

<script setup>
import { reactive, ref } from 'vue'

const prompt = ref(false)
const model = ref('select job title')
const department = ref('select department')
const date = ref('')
const jobOptions = ref([
  'Executive Director',
  'HR Officer',
  'Operation head',
  'Graphic artist'
])

const depOptions = ref(['Management', 'Operation', 'Executive'])

const credentials = reactive({
  email: '',
  password: '',
  personal_information: {
    firstname: '',
    middlename: '',
    lastname: '',
    gender: 'Select gender',
    birth_date: '',
    email:'',
    address: '',
    contact_number: '',
    contact_person: {
      name: '',
      address: '',
      contact_number: '',
      relationship: ''
    },
    ss_no: '',
    pagibig_no: '',
    philhealth: ''
  },
  employment_details: {
    job_title: 'select title',
    department: 'select department'
  },
  salary: {
    wage: '',
    basis: '',
    frequency: '',
    leave_entitlement: ''
  },
  legal_compliance: {
    contact: '',
    pre_employment: '',
    training_certificates: ''
  },
  performance: {
    review: '',
    actions: ''
  }
})

const step = ref(1)
</script>
