<script lang="ts" setup>
import { ErrorMessage } from "vee-validate";
import { toValue } from "vue";

import { useFormField } from "./useFormField";

const { name, formMessageId } = useFormField();
</script>

<template>
	<ErrorMessage
		:id="formMessageId"
		as="p"
		class="text-[0.8rem] font-medium text-destructive"
		:name="toValue(name)"
	/>
</template>
