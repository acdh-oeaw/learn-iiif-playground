<script lang="ts" setup>
import 'tify'
import 'tify/dist/tify.css'

import { Vue3JsonEditor } from "vue3-json-editor";

const viewer = ref(null);

defineRouteRules({
	prerender: true,
});

const t = useTranslations();

usePageMetadata({
	title: t("IndexPage.meta.title"),
});

const json = ref({"@context":"http://iiif.io/api/presentation/3/context.json","id":"https://iiif.harvardartmuseums.org/manifests/object/299843","type":"Manifest","behavior":["individuals"],"metadata":[{"label":{"none":["Date"]},"value":{"none":["1888"]}},{"label":{"none":["Classification"]},"value":{"none":["Paintings"]}},{"label":{"none":["Credit Line"]},"value":{"none":["Harvard Art Museums/Fogg Museum, Bequest from the Collection of Maurice Wertheim, Class of 1906"]}},{"label":{"none":["Object Number"]},"value":{"none":["1951.65"]}},{"label":{"none":["People"]},"value":{"none":["Artist: Vincent van Gogh, Dutch, 1853 - 1890"]}},{"label":{"none":["Medium"]},"value":{"none":["Oil on canvas"]}},{"label":{"none":["Technique"]},"value":{"none":["Nature print"]}},{"label":{"none":["Dimensions"]},"value":{"none":["61.5 x 50.3 cm (24 3/16 x 19 13/16 in.)\r\nframed: 90.4 x 79.7 x 8.3 cm (35 9/16 x 31 3/8 x 3 1/4 in.)"]}},{"label":{"none":["Provenance"]},"value":{"none":["Vincent van Gogh, Arles, (1888,) gift;  to Paul Gauguin, (1888-1897) sold. [Ambroise Vollard, Paris.] [Paul Cassirer Gallery, Berlin.] Dr. Hugo von Tschudi, Berlin, (1906-1911), by descent; to his widow, Angela von Tschudi, Munich (1911-1919),  to Neue Staatsgalerie, Munich (1919-1938); removed from the collection by the National Socialist (Nazi) authorities in 1938, (EK16554) consigned; to [Theodor Fischer Gallery, Lucerne, Switzerland, for sale June 30, 1939, lot 45]; to Maurice Wertheim (1939-1951) bequest; to Fogg Art Museum, 1951.\r\n\r\n \r\n\r\nNotes:\r\nGauguin sold the painting for Fr 300\r\nHugo von Tschudi bought the painting for the Nationalgalerie, Berlin, with funds from sponsors, but did not submit it to the Kaiser for pre-approval. He took the painting to Munich when he assumed a post there.\r\nAccording to Stephanie Barron, the van Gogh was removed from the Neue Staatsgalerie on March 27, 1938 and stored at Schloss Niederschönhausen in August of that year. (Barron, 1991, pp. 135-146)\r\n"]}}],"label":{"none":["Self-Portrait Dedicated to Paul Gauguin"]},"requiredStatement":{"label":{"none":["Attribution"]},"value":{"none":["Harvard Art Museums"]}},"thumbnail":[{"id":"https://ids.lib.harvard.edu/ids/iiif/47174896/full/!170,170/0/default.jpg","type":"Image","service":[{"@id":"https://ids.lib.harvard.edu/ids/iiif/47174896","@type":"ImageService2","profile":"level2"}]}],"provider":[{"id":"http://example.org/provider","type":"Agent","logo":[{"id":"https://ids.lib.harvard.edu/ids/iiif/437958013/full/!800,800/0/default.jpg","type":"Image","service":[{"@id":"https://ids.lib.harvard.edu/ids/iiif/437958013","@type":"ImageService2","profile":"level2"}]}],"label":{"none":["Unknown"]}}],"partOf":[{"id":"https://www.harvardartmuseums.org/collections","type":"Collection"}],"rendering":[{"id":"https://www.harvardartmuseums.org/collections/object/299843","type":"Text","format":"text/html","label":{"none":["Full record view"]}}],"items":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/canvas/canvas-47174896","type":"Canvas","height":2550,"width":2087,"label":{"none":["1"]},"annotations":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/list/47174896","type":"AnnotationPage"}],"items":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/canvas/canvas-47174896/annotation-page","type":"AnnotationPage","items":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/annotation/anno-47174896","type":"Annotation","motivation":"painting","target":"https://iiif.harvardartmuseums.org/manifests/object/299843/canvas/canvas-47174896","body":{"id":"https://ids.lib.harvard.edu/ids/iiif/47174896/full/full/0/default.jpg","type":"Image","height":2550,"width":2087,"format":"image/jpeg","service":[{"@id":"https://ids.lib.harvard.edu/ids/iiif/47174896","@type":"ImageService2","profile":"level2"}]}}]}],"page":1},{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/canvas/canvas-18737483","type":"Canvas","height":2550,"width":2088,"label":{"none":["2"]},"annotations":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/list/18737483","type":"AnnotationPage"}],"items":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/canvas/canvas-18737483/annotation-page","type":"AnnotationPage","items":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/annotation/anno-18737483","type":"Annotation","motivation":"painting","target":"https://iiif.harvardartmuseums.org/manifests/object/299843/canvas/canvas-18737483","body":{"id":"https://ids.lib.harvard.edu/ids/iiif/18737483/full/full/0/default.jpg","type":"Image","height":2550,"width":2088,"format":"image/jpeg","service":[{"@id":"https://ids.lib.harvard.edu/ids/iiif/18737483","@type":"ImageService2","profile":"level2"}]}}]}],"page":2},{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/canvas/canvas-47174892","type":"Canvas","height":2550,"width":2259,"label":{"none":["3"]},"annotations":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/list/47174892","type":"AnnotationPage"}],"items":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/canvas/canvas-47174892/annotation-page","type":"AnnotationPage","items":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/annotation/anno-47174892","type":"Annotation","motivation":"painting","target":"https://iiif.harvardartmuseums.org/manifests/object/299843/canvas/canvas-47174892","body":{"id":"https://ids.lib.harvard.edu/ids/iiif/47174892/full/full/0/default.jpg","type":"Image","height":2550,"width":2259,"format":"image/jpeg","service":[{"@id":"https://ids.lib.harvard.edu/ids/iiif/47174892","@type":"ImageService2","profile":"level2"}]}}]}],"page":3},{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/canvas/canvas-43182083","type":"Canvas","height":2550,"width":2100,"label":{"none":["4"]},"annotations":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/list/43182083","type":"AnnotationPage"}],"items":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/canvas/canvas-43182083/annotation-page","type":"AnnotationPage","items":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/annotation/anno-43182083","type":"Annotation","motivation":"painting","target":"https://iiif.harvardartmuseums.org/manifests/object/299843/canvas/canvas-43182083","body":{"id":"https://ids.lib.harvard.edu/ids/iiif/43182083/full/full/0/default.jpg","type":"Image","height":2550,"width":2100,"format":"image/jpeg","service":[{"@id":"https://ids.lib.harvard.edu/ids/iiif/43182083","@type":"ImageService2","profile":"level2"}]}}]}],"page":4},{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/canvas/canvas-43183405","type":"Canvas","height":2550,"width":2082,"label":{"none":["5"]},"annotations":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/list/43183405","type":"AnnotationPage"}],"items":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/canvas/canvas-43183405/annotation-page","type":"AnnotationPage","items":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/annotation/anno-43183405","type":"Annotation","motivation":"painting","target":"https://iiif.harvardartmuseums.org/manifests/object/299843/canvas/canvas-43183405","body":{"id":"https://ids.lib.harvard.edu/ids/iiif/43183405/full/full/0/default.jpg","type":"Image","height":2550,"width":2082,"format":"image/jpeg","service":[{"@id":"https://ids.lib.harvard.edu/ids/iiif/43183405","@type":"ImageService2","profile":"level2"}]}}]}],"page":5},{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/canvas/canvas-43183422","type":"Canvas","height":2550,"width":2093,"label":{"none":["6"]},"annotations":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/list/43183422","type":"AnnotationPage"}],"items":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/canvas/canvas-43183422/annotation-page","type":"AnnotationPage","items":[{"id":"https://iiif.harvardartmuseums.org/manifests/object/299843/annotation/anno-43183422","type":"Annotation","motivation":"painting","target":"https://iiif.harvardartmuseums.org/manifests/object/299843/canvas/canvas-43183422","body":{"id":"https://ids.lib.harvard.edu/ids/iiif/43183422/full/full/0/default.jpg","type":"Image","height":2550,"width":2093,"format":"image/jpeg","service":[{"@id":"https://ids.lib.harvard.edu/ids/iiif/43183422","@type":"ImageService2","profile":"level2"}]}}]}],"page":6}]});

const onJsonChange = (json: any) => {
	viewer.value.app.config.globalProperties.$store.manifest = null;
	viewer.value.app.config.globalProperties.$store.manifest = json;
	console.log(viewer.value.app.config.globalProperties.$store.manifest);
};

onMounted(async ()=> {
	viewer.value = new Tify({
		container: '#viewer',
		language: 'en',
		manifestUrl: "https://iiif.harvardartmuseums.org/manifests/object/299843"
	})
})
</script>

<template>
	<MainContent class="container grid content-start gap-y-8 py-8">
		<PageTitle>IIIF Presentation API</PageTitle>
		<div class="flex" >
		<div>
			<Vue3JsonEditor
				class="h-screen "
				v-model="json"
				:expanded-on-start="true"
				:show-btns="true"
				@json-save="onJsonChange"
			/>
		</div>
		<div id="viewer" class="w-1/2 h-1/2"></div>
		</div>
	</MainContent>
</template>
