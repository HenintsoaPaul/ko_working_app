<script setup>
const formState = reactive({
    email: '',
    password: ''
});

const onSubmit = () => {
    console.log("form: ", formState);
};
</script>

<template>
    <div>
        <UForm :state="formState" @submit="onSubmit">
            <UFormGroup label="Email" name="email">
                <UInput v-model="formState.email" type="email" />
            </UFormGroup>

            <UFormGroup label="Password" name="password">
                <UInput v-model="formState.password" type="password" />
            </UFormGroup>

            <UButton type="submit">
                Submit
            </UButton>
        </UForm>
    </div>
</template>

<style></style>