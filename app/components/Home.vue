<template>
	<Page>
		<ActionBar>
			<Label text="Home"></Label>
		</ActionBar>

		<GridLayout>
			<Label class="info" @tap="onTapLabel">
				<FormattedString>
					<Span class="fas" text.decode="&#xf135; "/>
					<Span :text="message"/>
				</FormattedString>
			</Label>
		</GridLayout>
	</Page>
</template>

<script>

	import {alert} from 'tns-core-modules/ui/dialogs';
  import {openUrl} from 'tns-core-modules/utils/utils';
  import InAppBrowser from 'nativescript-inappbrowser';

	const openBrowser = async () => {
		try {

		  const url = "https://online-media.ru";
			if (await InAppBrowser.isAvailable()) {

			    // Here will be a browser opening

			} else {
				openUrl(url);
			}

		} catch (ex) {
			alert({
				title: 'Error :(',
				message: ex.message,
				okButtonText: 'Dismiss',
			});
		}
	};

	export default {
		methods: {
			onTapLabel() {
				console.log('Opa');
				openBrowser();
			}
		},
		computed: {
			message() {
				return "Blank {N} app";
			}
		}
	};
</script>

<style scoped lang="scss">
	// Custom styles
	.fas {
		color: accent;
	}

	.info {
		font-size: 20;
		horizontal-align: center;
		vertical-align: center;
	}
</style>
