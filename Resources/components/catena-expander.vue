<template>
	<div :class="{'catena-expander':true, 'expanded': expanded}">
		<button class="handle" @click="expand(!expanded)"><i :class="iconClass" v-if="icon !== null"></i> {{title}}<template v-if="!expanded">&hellip;</template></button>
		<div v-if="expanded">
			<slot/>
		</div>
	</div>
</template>

<script>
module.exports = {
	props: {
		title: String,
		icon: { type: String, default: null }
	},

	data: function() {
		return { expanded: false };
	},

	computed: {
		iconClass: function() {
			return "fa fa-" + this.icon;
		}
	},

	methods: {
		expand: function(e) {
			this.expanded = e;
		}
	}
};
</script>