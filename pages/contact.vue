<script setup lang="ts">
const { data: contact } = await useAsyncData(() =>
	queryCollection("content").path("/contact").first()
);

useSeoMeta({
	title: contact.value?.title,
	description: contact.value?.description,
});
</script>

<template>
	<div class="contact-page">
		<ContentRenderer v-if="contact" :value="contact" class="contact-content" />
		<div v-else>Contact page not found</div>
	</div>
</template>

<style>
.contact-page {
	max-width: 800px;
	margin: auto;
	padding: 20px;
	background: #f9f9f9;
	border-radius: 8px;
	box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

.contact-content h1 {
	color: red;
	text-align: center;
}

.contact-content .contact-form {
	display: flex;
	flex-direction: column;
	gap: 1rem;
	color: red;
}
</style>
