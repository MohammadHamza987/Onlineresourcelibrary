<template>
	<li>
		<base-card>
			<div class="resource-content">
				<header class="resource-header">
					<h3>{{ title }}</h3>
					<base-button mode="flat" @click="$emit('delete-resource', id)" class="delete-btn">Delete</base-button>
				</header>
				<p class="resource-description">{{ description }}</p>
				<nav class="resource-nav">
					<a :href="link" target="_blank" rel="noopener noreferrer">View Resource</a>
				</nav>
			</div>
    </base-card>
	</li>
</template>

<script>
export default {
	props: {
		id: String,
		title: String,
		description: String,
		link: String
	},
	emits: ['delete-resource']
};
</script>
<style scoped>
li {
	margin-bottom: 24px;
	padding: 0;
	border: none;
	border-radius: 16px;
	background: none;
	box-shadow: none;
	transform-origin: center;
	transition: transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
}

li:hover {
	transform: scale(1.02);
}

.resource-content {
	position: relative;
}

.resource-header {
	display: flex;
	justify-content: space-between;
	align-items: flex-start;
	margin-bottom: 1rem;
	gap: 12px;
}

h3 {
	margin: 0;
	font-size: 1.3rem;
	font-weight: 700;
	background: linear-gradient(135deg, #ec4899 0%, #a855f7 100%);
	-webkit-background-clip: text;
	-webkit-text-fill-color: transparent;
	background-clip: text;
	text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
	flex: 1;
}

.delete-btn {
	flex-shrink: 0;
}

.resource-nav {
	margin-top: 16px;
}

.resource-nav a {
	color: #ec4899;
	text-decoration: none;
	font-weight: 600;
	font-size: 1.05rem;
	padding: 10px 20px;
	background: rgba(13, 17, 23, 0.6);
	backdrop-filter: blur(10px);
	border-radius: 8px;
	border: 1px solid rgba(236, 72, 153, 0.3);
	transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
	display: inline-block;
	box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
}

.resource-nav a:hover {
	background: rgba(219, 39, 119, 0.2);
	transform: translateY(-2px);
	box-shadow: 0 6px 20px rgba(219, 39, 119, 0.3);
	border-color: rgba(236, 72, 153, 0.6);
	color: #ffffff;
}

.resource-description {
	margin: 0;
	color: rgba(255, 255, 255, 0.8);
	font-size: 1rem;
	line-height: 1.6;
	text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}

@media (max-width: 768px) {
	li {
		margin-bottom: 20px;
	}
	.resource-header {
		flex-direction: column;
		align-items: stretch;
		gap: 12px;
		margin-bottom: 0.8rem;
	}
	h3 {
		font-size: 1.2rem;
		margin-bottom: 8px;
		text-align: center;
	}
	.delete-btn {
		align-self: center;
		padding: 8px 16px !important;
		font-size: 0.85rem !important;
	}
	.resource-nav {
		margin-top: 12px;
		text-align: center;
	}
	.resource-nav a {
		padding: 10px 18px;
		font-size: 0.95rem;
		display: block;
		width: 100%;
		text-align: center;
		box-sizing: border-box;
	}
	.resource-description {
		font-size: 0.95rem;
		line-height: 1.5;
		text-align: center;
	}
}

@media (max-width: 480px) {
	li {
		margin-bottom: 16px;
	}
	.resource-header {
		gap: 8px;
	}
	h3 {
		font-size: 1.1rem;
	}
	.resource-nav a {
		padding: 6px 12px;
		font-size: 0.85rem;
		border-radius: 6px;
	}
	.resource-nav a:hover {
		transform: translateY(-1px);
	}
	.resource-description {
		font-size: 0.9rem;
	}
}
</style>