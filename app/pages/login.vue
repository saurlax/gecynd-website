<script setup lang="ts">
import type { AuthFormField, FormSubmitEvent } from "@nuxt/ui";
import { z } from "zod";

const supabase = useSupabaseClient();

const fields: AuthFormField[] = [
  {
    name: "email",
    type: "email",
    label: "Email",
    placeholder: "Enter your email",
    required: true,
  },
  {
    name: "password",
    label: "Password",
    type: "password",
    placeholder: "Enter your password",
    required: true,
  },
  {
    name: "remember",
    label: "Remember me",
    type: "checkbox",
  },
];

const schema = z.object({
  email: z.email(),
  password: z.string().min(6),
});

function login(payload: FormSubmitEvent<z.output<typeof schema>>) {
  const { email, password } = payload.data;
  supabase.auth.signInWithPassword({ email, password });
}
</script>

<template>
  <UContainer>
    <UPageBody>
      <UPageCard class="max-w-md m-auto">
        <UAuthForm :fields="fields" title="Login" @submit.prevent="login" />
      </UPageCard>
    </UPageBody>
  </UContainer>
</template>
