<template>
    <Form @submit="onSubmit" :validation-schema="formSchema">
        <div class="mb-3">
            <label for="name">Name</label>
            <Field 
              name="name" 
              placeholder="Enter your name"
              class="form-control"  
            />
            <ErrorMessage name="name" as="div" v-slot="{message}">
              <div class="alert alert-danger" role="alert">
                {{ message }}
              </div>
            </ErrorMessage>
        </div>

        <button class="btn btn-primary">
          Submit
        </button>
    </Form>
</template>

<script setup>
  import { Field, Form, ErrorMessage } from 'vee-validate';
  import * as yup from 'yup';

  const formSchema = yup.object({
    name:yup.string()
    .required('The name is required')
    .max(5,'Sorry a max of 5')
  })

  function onSubmit(values,{ resetForm }){
    console.log(values);
    resetForm();
  }


  // const isRequired = (value) =>{
  //     if(!value) { return 'This field is required'}
  //     return true;
  // }

  // const validateName = (value) => {
  //   if(value !== 'steve'){ return true }
  //   return 'You are not allowed steve !!!'
  // }




</script>