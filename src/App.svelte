<script>
	import FeedbackList from "./components/FeedbackList.svelte";

	let feedback = [
		{
			id: 1,
			rating: 10,
			text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Magni ipsam culpa perferendis itaque modi inventore cupiditate. Recusandae sint cumque iste libero expedita vel quaerat, placeat, sunt saepe atque maiores id.'
		},
		{
			id: 2,
			rating: 8,
			text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Magni ipsam culpa perferendis itaque modi inventore cupiditate. Recusandae sint cumque iste libero expedita vel quaerat, placeat, sunt saepe atque maiores id.'
		},
		{
			id: 3,
			rating: 9,
			text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Magni ipsam culpa perferendis itaque modi inventore cupiditate. Recusandae sint cumque iste libero expedita vel quaerat, placeat, sunt saepe atque maiores id.'
		}
	]

	const deleteFeedback = (e) => {
		const itemId = e.detail
		feedback = feedback.filter((item) => item.id != itemId)
	}
</script>

<main class="container">
	<FeedbackList {feedback} on:delete-feedback = {deleteFeedback}/>
</main>