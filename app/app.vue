<script setup lang="ts">
useHead({
  title: '🟢 Włancznik – interaktywny przełącznik',
  meta: [
    { name: 'description', content: 'Włącznik światła z animowanym przełącznikiem i dynamicznym statusem.' },

    // Open Graph (Facebook, LinkedIn)
    { property: 'og:title', content: '🟢 Włancznik – interaktywny przełącznik' },
    { property: 'og:description', content: 'Kliknij i zobacz, jak działa interaktywny włącznik!' },
    { property: 'og:image', content: 'https://example.com/wlancznik-social.jpg' }, // podmień
    { property: 'og:url', content: 'https://example.com/' },
    { property: 'og:type', content: 'website' },

    // Twitter Card
    { name: 'twitter:card', content: 'summary_large_image' },
    { name: 'twitter:title', content: '🟢 Włancznik – interaktywny przełącznik' },
    { name: 'twitter:description', content: 'Zabawny i funkcjonalny włącznik do testów UI.' },
    { name: 'twitter:image', content: 'https://example.com/wlancznik-social.jpg' }
  ]
});
onMounted(() => {
  const checkbox = document.getElementById('toggleSwitch');
  const statusText = document.getElementById('statusText');
  checkbox.addEventListener('change', () => {
    statusText.textContent = checkbox.checked ? 'Status: Włanczone 🔆' : 'Status: Wyłanczone 🌑';
  });

})
</script>

<template>
  <div>
    <h1>🟢 Włancznik</h1>

    <div class="switch-wrapper">
      <div class="switch-label">Włanczaj:</div>
      <label class="switch">
        <input type="checkbox" id="toggleSwitch">
        <span class="slider"></span>
      </label>
      <div class="status" id="statusText">Status: wyłączone</div>
    </div>

  </div>
</template>

<style lang="scss">
body {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f0f0f0;
}

h1 {
  margin-bottom: 40px;
  font-size: 2em;
}

.switch-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.switch-label {
  margin-bottom: 15px;
  font-size: 1.2em;
  font-weight: bold;
}

.switch {
  position: relative;
  width: 70px;
  height: 36px;
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  background-color: #ccc;
  transition: 0.4s;
  border-radius: 34px;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}

.slider:before {
  position: absolute;
  content: "";
  height: 28px;
  width: 28px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  transition: 0.4s;
  border-radius: 50%;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
}

input:checked+.slider {
  background-color: #4caf50;
}

input:checked+.slider:before {
  transform: translateX(34px);
}

.status {
  margin-top: 20px;
  font-size: 1.1em;
}
</style>