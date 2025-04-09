<script lang="ts" setup>
import { Vue3JsonEditor } from "vue3-json-editor";

defineRouteRules({
	prerender: true,
});

const t = useTranslations();

usePageMetadata({
	title: t("IndexPage.meta.title"),
});

const json = ref({
	"@context": "https://iiif.io/api/presentation/2/context.json",
	"@id": "https://demo.openatlas.eu/api/iiif_manifest/2/15948",
	"@type": "sc:Manifest",
	attribution: "",
	description: [
		{
			"@language": "en",
			"@value": "",
		},
	],
	label: "dfsa",
	license: "",
	logo: {
		"@id": "https://demo.openatlas.eu/api/display/",
		service: {
			"@context": "https://iiif.io/api/image/2/context.json",
			"@id": "https://demo.openatlas.eu/overview",
			profile: "https://iiif.io/api/image/2/level2.json",
		},
	},
	metadata: [],
	seeAlso: [
		{
			"@id": "https://frontend-demo.openatlas.eu/en/entity/5233",
			format: "Source",
			label: "Absagebrief ulrichs von eitzing vom 1441 mai 12",
		},
	],
	sequences: [
		{
			"@id": "https://demo.openatlas.eu/api/iiif_sequence/15948.json",
			"@type": "sc:Sequence",
			canvases: [
				{
					"@id": "https://demo.openatlas.eu/api/iiif_canvas/15948.json",
					"@type": "sc:Canvas",
					description: {
						"@language": "en",
						"@value": "",
					},
					height: 648,
					images: [
						{
							"@context": "https://iiif.io/api/presentation/2/context.json",
							"@id": "https://demo.openatlas.eu/api/iiif_image/15948.json",
							"@type": "oa:Annotation",
							motivation: "sc:painting",
							on: "https://demo.openatlas.eu/api/iiif_canvas/15948.json",
							resource: {
								"@id": "https://demo.openatlas.eu/iiif/demo/15948.tiff",
								"@type": "dctypes:Image",
								format: "image/jpeg",
								height: 648,
								service: {
									"@context": "https://iiif.io/api/image/2/context.json",
									"@id": "https://demo.openatlas.eu/iiif/demo/15948.tiff",
									profile: [
										"http://iiif.io/api/image/2/level1.json",
										{
											formats: ["jpg"],
											maxHeight: 5000,
											maxWidth: 5000,
											qualities: ["native", "color", "gray", "bitonal"],
											supports: [
												"regionByPct",
												"regionSquare",
												"sizeByForcedWh",
												"sizeByWh",
												"sizeAboveFull",
												"rotationBy90s",
												"mirroring",
											],
										},
									],
								},
								width: 1200,
							},
						},
					],
					label: "dfsa",
					otherContent: [
						{
							"@id": "https://demo.openatlas.eu/api/iiif_annotation_list/15948.json",
							"@type": "sc:AnnotationList",
						},
					],
					related: "",
					thumbnail: {
						"@id": "https://demo.openatlas.eu/iiif/demo/15948.tiff/full/!200,200/0/default.jpg",
						"@type": "dctypes:Image",
						format: "image/jpeg",
						height: 200,
						service: {
							"@context": "https://iiif.io/api/image/2/context.json",
							"@id": "https://demo.openatlas.eu/iiif/demo/15948.tiff",
							profile: [
								"http://iiif.io/api/image/2/level1.json",
								{
									formats: ["jpg"],
									maxHeight: 5000,
									maxWidth: 5000,
									qualities: ["native", "color", "gray", "bitonal"],
									supports: [
										"regionByPct",
										"regionSquare",
										"sizeByForcedWh",
										"sizeByWh",
										"sizeAboveFull",
										"rotationBy90s",
										"mirroring",
									],
								},
							],
						},
						width: 200,
					},
					width: 1200,
				},
			],
			label: [
				{
					"@language": "en",
					"@value": "Normal Sequence",
				},
			],
		},
	],
	structures: [],
});

const onJsonChange = (json: any) => {
	console.log(json);
};
</script>

<template>
	<MainContent class="container grid content-start gap-y-8 py-8">
		<PageTitle>IIIF Presentation API</PageTitle>
		<div>
			<div>Manifest JSON</div>
			<Vue3JsonEditor
				v-model="json"
				:expanded-on-start="true"
				:show-btns="true"
				@json-change="onJsonChange"
			/>
		</div>
	</MainContent>
</template>
