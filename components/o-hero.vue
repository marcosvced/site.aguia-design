<script setup lang="js">
const download = async () => {
  const {data} = await useFetch('assets/aguia-zip/aguia.zip', {method: 'get', responseType: 'blob'})
  console.log(data)
  forceFileDownload(data)
}
const forceFileDownload = (response) => {
  const url = window.URL.createObjectURL(new Blob([response.data]))
  const link = document.createElement('a')
  link.href = url
  link.setAttribute('download', 'aguia@1.5.0.zip') //or any other extension
  document.body.appendChild(link)
  link.click()
}
</script>
<template>
  <section class="o-hero -mb-5">
    <div class="m-hero__wrapper -container">
      <div class="-display-row -gap -wrap -justify-between -align-start">
        <div class="m-hero__title -display-column -col-12 -ip-col-7">
          <h1 class="a-hero__title">
            Aguia<br/> Design System
          </h1>
          <p class="-m-0 -mb-1">Do you like Aguia and want to Tweet it, share it, or star it?</p>
          <p class="-display-row -m-0 -mb-2 -align-center">Well, I appreciate that <i class="a-icon -smile -ml-1"/></p>
          <div class="-display-row">
            <div class="-mr-1">
              <a class="twitter-share-button" href="https://twitter.com/share?ref_src=twsrc%5Etfw" data-size="large"
                 data-text="Aguia Design System: a simple responsive framework" data-url="https://aguia-design.ga"
                 data-show-count="true">Tweet</a>
            </div>
            <div class="-mr-1">
              <a class="github-button" href="https://github.com/marcosvced/Aguia-Design"
                 data-color-scheme="no-preference: dark; light: dark; dark: dark;" data-icon="octicon-star"
                 data-size="large" data-show-count="true" aria-label="Star marcosvced/Aguia-Design on GitHub">Star</a>
            </div>
            <a class="github-button" href="https://github.com/marcosvced/Aguia-Design/fork"
               data-color-scheme="no-preference: dark; light: dark; dark: dark;" data-icon="octicon-repo-forked"
               data-size="large" data-show-count="true" aria-label="Fork marcosvced/Aguia-Design on GitHub">Fork</a>
          </div>
        </div>
        <div class="m-hero__content -col-12 -md-col-7 -ip-col-5">
          <header class="m-header -col-12 -mb-2">
            <p class="a-header__abstract">INTRODUCTION</p>
            <h2 class="a-header__tile">A simple responsive framework</h2>
            <p class="a-header__description">
              that offers a starting point in which you won't need to fight with the unnecessary default styles of other
              frameworks.
              With this tool you will be able to organize your code using the ABEM methodology that you can customize as
              never before.
            </p>
          </header>
          <a class="a-button -btn-link" @click="download">Download <i class="a-icon -arrow-right"></i></a>
          <p>or <code class="a-code -code-inline -dark">npm i @devler/aguia-css</code></p>
        </div>
      </div>
    </div>
  </section>
</template>
