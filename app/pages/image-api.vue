<script lang="ts" setup>

import { toTypedSchema } from '@vee-validate/zod'
import { useForm } from 'vee-validate'
import * as z from 'zod'

defineRouteRules({
	prerender: true,
});

const t = useTranslations();
const imgurl = ref("https://loris.acdh.oeaw.ac.at/1056605/full/720,/0/default.jpg");
const imgwidth = ref("auto");
const imgheight = ref("auto");

usePageMetadata({
	title: t("IndexPage.meta.title"),
});

const formSchema = toTypedSchema(z.object({
	server: z.string().url(),
	identifier: z.string(),
	region: z.string(),
	size: z.string(),
	rotation: z.string(),
	quality: z.string(),
	format: z.string(),
}))

const { isFieldDirty, handleSubmit } = useForm({
	validationSchema: formSchema,
})

const onSubmit = handleSubmit((values) => {
	console.log(values);
	imgurl.value = `${values.server}/${values.identifier}/${values.region}/${values.size}/${values.rotation}/${values.quality}.${values.format}`;
	imgwidth.value = values.size.split(",")[0];
	imgheight.value = values.size.split(",")[1];
})
</script>

<template>
	<MainContent class="container grid content-start gap-y-8 py-8">
		<PageTitle>IIIF Image API</PageTitle>
		<form class="w-2/3 space-y-6 flex  items-stretch" @submit="onSubmit">
			<div className=""></div>
			<FormField v-slot="{ componentField }" name="server" :validate-on-blur="!isFieldDirty">
				<FormItem>
					<FormLabel class="font-semibold">Server</FormLabel>
					<FormControl>
						<Input placeholder="https://loris.acdh.oeaw.ac.at" type="text" v-bind="componentField" list="listOfServers"/>
						<datalist id="listOfServers">
							<option value="https://loris.acdh.oeaw.ac.at"></option>
						</datalist>
					</FormControl>
					<FormMessage />
				</FormItem>
			</FormField>
			<div className="pt-9 font-black">/</div>
			<FormField v-slot="{ componentField }" name="identifier">
				<FormItem>
					<FormLabel class="font-semibold">Identifier</FormLabel>
					<FormControl>
						<Input placeholder="" type="text" v-bind="componentField" list="listOfIdentifiers" />
						<datalist id="listOfIdentifiers">
							<option value="1056605"></option>
							<option value="540584"></option>
						</datalist>
					</FormControl>
					<FormMessage />
				</FormItem>
			</FormField>
			<div className="pt-9 font-black">/</div>
			<FormField v-slot="{ componentField }" name="region">
				<FormItem>
					<FormLabel class="font-semibold">Region</FormLabel>
					<FormControl>
						<Input placeholder="" type="text" v-bind="componentField" list="listOfRegions" />
						<datalist id="listOfRegions">
							<option value="full"></option>
							<option value="square"></option>
							<option value="125,15,120,140"></option>
							<option value="pct:41.6,7.5,40,70"></option>
						</datalist>
					</FormControl>
					<FormMessage />
				</FormItem>
			</FormField>
			<div className="pt-9 font-black">/</div>
			<FormField v-slot="{ componentField }" name="size">
				<FormItem>
					<FormLabel class="font-semibold">Size</FormLabel>
					<FormControl>
						<Input placeholder="" type="text" v-bind="componentField" list="listOfSizes" />
						<datalist id="listOfSizes">
							<option value="150,">scaled to width</option>
							<option value=",150">scaled to height</option>
							<option value="150,150"></option>
							<option value="!150,150"></option>
							<option value="pct:50"></option>
						</datalist>
					</FormControl>
					<FormMessage />
				</FormItem>
			</FormField>
			<div className="pt-9 font-black">/</div>
			<FormField v-slot="{ componentField }" name="rotation">
				<FormItem>
					<FormLabel class="font-semibold">Rotation</FormLabel>
					<FormControl>
						<Input placeholder="" type="text" v-bind="componentField" list="listOfRotations" />
						<datalist id="listOfRotations">
							<option value="90">clockwise</option>
							<option value="!90">mirrored</option>
						</datalist>
					</FormControl>
					<FormMessage />
				</FormItem>
			</FormField>
			<div className="pt-9 font-black">/</div>
			<FormField v-slot="{ componentField }" name="quality">
				<FormItem>
					<FormLabel class="font-semibold">Quality</FormLabel>
					<FormControl>
						<Input placeholder="" type="text" v-bind="componentField" list="listOfQualities" />
						<datalist id="listOfQualities">
							<option value="color"></option>
							<option value="gray"></option>
							<option value="bitonal"></option>
							<option value="default"></option>
						</datalist>
					</FormControl>
					<FormMessage />
				</FormItem>
			</FormField>
			<div className="pt-9 font-black">.</div>
			<FormField v-slot="{ componentField }" name="format">
				<FormItem>
					<FormLabel class="font-semibold">Format</FormLabel>
					<FormControl>
						<Input placeholder="" type="text" v-bind="componentField" list="listOfFormats" />
						<datalist id="listOfFormats">
							<option value="jpg"></option>
							<option value="png"></option>
							<option value="webp"></option>
						</datalist>
					</FormControl>
					<FormMessage />
				</FormItem>
			</FormField>
			<Button type="submit">
				Submit
			</Button>
		</form>
		<img :src="imgurl" :width="imgwidth" :height="imgheight" alt="Image" />
	</MainContent>
</template>
