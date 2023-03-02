<svelte:options tag="pi-custom-banner2" />

<script>
  // @ts-nocheck

  async function loadjscssfile(filename, filetype) {
    return new Promise((resolve, reject) => {
      let cssNode;
      if (filetype == "js") {
        cssNode = document.createElement("script");
        cssNode.setAttribute("type", "text/javascript");
        cssNode.setAttribute("src", filename);
        cssNode.defer = true;
      } else if (filetype == "css") {
        cssNode = document.createElement("link");
        cssNode.setAttribute("rel", "stylesheet");
        cssNode.setAttribute("type", "text/css");
        cssNode.setAttribute("href", filename);
      }
      if (typeof cssNode != "undefined") {
        document.getElementsByTagName("head")[0].appendChild(cssNode);
      }
      cssNode.onload = () => {
        console.log("1001010100");
        return resolve();
      };
    });
  }
  loadjscssfile("https://unpkg.com/swiper/swiper-bundle.min.css", "css");
  loadjscssfile("https://unpkg.com/swiper/swiper-bundle.min.js", "js").then(
    () => {
      const a = document.querySelector(".piBusinessSwiper");
      console.log("222222", a, Swiper);
      if (window.Swiper) {
        const businessSwiper = new Swiper(".piBusinessSwiper", {
          loop: true,
          noSwiping: true,
          noSwipingClass: "swiper-no-swiping",
          centeredSlides: true,
          autoplay: {
            delay: 5000,
            disableOnInteraction: false,
          },
          pagination: {
            el: ".swiper-ban-pagination",
            clickable: true,
          },
        });
      }
    }
  );

  // window.addEventListener("DOMContentLoaded", () => {});

  function handleJapanbanner() {
    const lang = document.getElementsByTagName("html")[0].getAttribute("lang");
    console.log("----", lang);
    if (lang == "ja") {
      switchImageBy("piCustomImage");
    }
  }

  function switchImageBy(id) {
    const target = document.getElementById(id);
    target.setAttribute("href", "/product/mystery-box-outlet-headset-jp/");
    const sourceList = target.querySelectorAll("picture source");
    const sourceUrls = {
      pc: "https://pimax.com/wp-content/uploads/2023/02/ja-banner-p.jpg",
      mobile: "https://pimax.com/wp-content/uploads/2023/02/ja-banner-m.jpg",
    };
    sourceList.forEach((source) => {
      if (source.dataset.type) {
        source.setAttribute("srcset", sourceUrls[source.dataset.type]);
      }
    });
  }

  handleJapanbanner();
</script>

<div class="pi-news-swiper-c">
  <div class="pi-news-container">
    <div class="swiper piBusinessSwiper">
      <div class="swiper-wrapper">
        <div class="swiper-slide">
          <a
            id="piCustomImage"
            style="display: block;position: relative;max-width:1920px; margin: 0 auto;cursor: pointer;"
            href="https://pimax.com/product/mystery-box-outlet-headset/"
          >
            <picture class="Launch-item-picture">
              <source
                data-type="pc"
                srcset="https://pimax.com/wp-content/uploads/2023/02/mystery-b-pc.jpg"
                media="(min-width:518px)"
              />
              <source
                data-type="mobile"
                srcset="https://pimax.com/wp-content/uploads/2023/02/mystery-b-m.jpg"
                media="(max-width:517px)"
              />
              <img
                class="lazy-load-active"
                decoding="async"
                src="https://pimax.com/wp-content/uploads/2023/02/mystery-b-m.jpg"
                data-src="https://pimax.com/wp-content/uploads/2023/02/mystery-b-m.jpg"
                alt="pimax myster"
              />
            </picture>
          </a>
        </div>
        <div class="swiper-slide">
          <a
            style="display: block;position: relative;max-width:1920px; margin: 0 auto;cursor: pointer;"
            href="https://pimax.com/portal/"
          >
            <picture class="Launch-item-picture">
              <source
                srcset="https://pimax.com/wp-content/uploads/2022/12/电脑端banner.png"
                media="(min-width:518px)"
              />
              <source
                srcset="https://pimax.com/wp-content/uploads/2022/12/手机端banner.png"
                media="(max-width:517px)"
              />
              <img
                class="lazy-load-active"
                decoding="async"
                src="https://pimax.com/wp-content/uploads/2022/12/手机端banner.png"
                data-src="https://pimax.com/wp-content/uploads/2022/12/手机端banner.png"
                alt="pimax frontier"
              />
            </picture>
          </a>
        </div>
      </div>
    </div>
    <div class="swiper-ban-pagination" />
  </div>
</div>

<style>
  @import "https://unpkg.com/swiper/swiper-bundle.min.css";

  .swiper-slide {
    display: block;
  }

  .swiper-slide img {
    max-width: 100%;
    width: 100%;
    height: 100%;
    object-fit: contain;
  }

  .pi-news-swiper-c {
    min-height: 300px;
    width: 100%;
    position: relative;
    background-color: rgba(35, 35, 38, 1);
  }

  .pi-news-container {
    max-width: 1920px;
    height: 100%;
    margin: 0 auto;
    position: relative;
  }

  .swiper-ban-pagination {
    position: absolute;
    text-align: center;
    transition: 0.3s opacity;
    transform: translate3d(0, 0, 0);
    z-index: 10;
  }

  .swiper-ban-pagination .swiper-pagination-bullet {
    background-color: #34c900;
    height: 6px;
    border-radius: 2px;
    width: 15px;
    opacity: 0.4;
  }

  .swiper-ban-pagination .swiper-pagination-bullet-active {
    opacity: 1;
  }
</style>
