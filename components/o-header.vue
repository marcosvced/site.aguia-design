<script setup lang="js">
const checkIfIsOnScreen = (item) => {
  const element = document.querySelector(`#${item.getAttribute('data-item')}`);
  return element.getBoundingClientRect().top <= (self.innerHeight / 2) && element.getBoundingClientRect().bottom
      + +self.getComputedStyle(element).marginBottom.replace('px', '') >= (self.innerHeight / 2);
}
const isDarkBackground = () => {
  const item = document.querySelector('.o-hero');
  const header = document.querySelector('.o-header');
  if (item.getBoundingClientRect().bottom <= header.offsetHeight) {
    header.classList.add('-background-dark');
    document.querySelector('meta[name="theme-color"]').content = '#252734';
  } else {
    header.classList.remove('-background-dark');
    document.querySelector('meta[name="theme-color"]').content = '#333646';
  }
}
const scrollToId = (id) => {
  const header = document.querySelector('.o-header');
  const target = document.querySelector(`#${id}`)
  document.scrollingElement.scroll({
    top: target.offsetTop - (self.innerHeight - header.offsetHeight) / 2,
    behavior: 'smooth'
  })
}
const scrollToTop = () => {
  document.scrollingElement.scroll({top: 0, behavior: 'smooth',})
}

if (process.client) {
  self.addEventListener("scroll", () => {
    const items = document.querySelectorAll('.o-header .m-nav .a-nav__item');
    items.forEach(item => {
      let isOnScreen = checkIfIsOnScreen(item);
      if (isOnScreen) {
        item.classList.add('-item-active');
      } else {
        item.classList.remove('-item-active');
      }
    });
    isDarkBackground();
  })
}

</script>

<template>
  <header class="o-header -md-position-sticky">
    <div class="m-header__wrapper -container -display-row -justify-between">
      <div class="a-logo__icon" @click="scrollToTop"></div>
      <ul class="m-nav -position-fixed -md-position-static">
        <li class="a-nav__item" data-item="layout" @click="scrollToId('layout')">
          <i class="a-icon -layers"></i>
          <span>Layout</span>
        </li>
        <li class="a-nav__item" data-item="responsive" @click="scrollToId('responsive')">
          <i class="a-icon -grid"></i><span>Responsive</span>
        </li>
        <li class="a-nav__item" data-item="modifiers" @click="scrollToId('modifiers')">
          <i class="a-icon -tool"></i><span>Modifiers</span>
        </li>
      </ul>
    </div>
  </header>
</template>

<style scoped>

</style>