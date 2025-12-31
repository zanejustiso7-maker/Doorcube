# Doorcube
A new social media site for posting stuff :)

<section id="readme-upload">
	<h3>Upload an image</h3>
	<input type="file" id="readmeImageInput" accept="image/*">
	<button id="readmeUploadBtn">Upload</button>
	<div id="readmePreview" style="margin-top:8px;"></div>
	<p><em>Note: This demo previews images client-side. No server storage included.</em></p>
</section>

<script>
document.addEventListener('DOMContentLoaded', function(){
	const input = document.getElementById('readmeImageInput');
	const preview = document.getElementById('readmePreview');
	const btn = document.getElementById('readmeUploadBtn');
	if(!input || !preview || !btn) return;
	input.addEventListener('change', () => {
		const file = input.files && input.files[0];
		preview.innerHTML = '';
		if (!file) return;
		if (!file.type.startsWith('image/')) {
			preview.textContent = 'Please select an image file.';
			return;
		}
		const img = document.createElement('img');
		img.src = URL.createObjectURL(file);
		img.alt = file.name;
		img.style.maxWidth = '300px';
		img.style.maxHeight = '200px';
		img.style.border = '1px solid #ccc';
		preview.appendChild(img);
	});
	btn.addEventListener('click', () => {
		if (!input.files || !input.files[0]) {
			alert('Select an image first.');
			return;
		}
		alert('Demo only: implement a server endpoint to save uploads.');
	});
});
</script>
