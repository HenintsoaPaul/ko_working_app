<script setup lang="ts">
import { z } from 'zod';
import type { FormSubmitEvent } from '#ui/types';

const schema = z.object({
    email: z.string().email('Invalid email'),
    password: z.string().min(3, 'Must be at least 3 characters')
});

type Schema = z.output<typeof schema>;

const formState = reactive({
    email: undefined,
    password: undefined
});

const onSubmit = (event: FormSubmitEvent<Schema>) => {
    console.log("form: ", event.data);
};
</script>

<template>
    <div>
        <UForm :schema="schema" :state="formState" @submit="onSubmit">
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