<script>
  // const colorThief = new ColorThief();
  const colorThief = new ColorThief();
  const img = document.querySelector('.img');
  console.log(img);
  // Make sure image is finished loading
  if (img.complete) {
    let color = colorThief.getColor(img);
    console.log(color);
  } else {
    image.addEventListener('load', function () {
      colorThief.getColor(img);
    });
  }
</script>

<main>
  <h2>Hello World</h2>
  <img
    class="img"
    alt="landscape"
    src="https://freight.cargo.site/w/750/i/5119154af544436a4e30a451a5586ce9a6fd462b9671d321a3eda093cda11225/R0001605.jpg"
  />
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  img {
    width: 100%;
    height: auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
