#


# 超連結的事件點擊範圍在 a 標籤的 content + padding 範圍內

# Q1
現在我的 picture 中的圖片，沒有緊貼左右兩側 viewport ，我希望這張圖片可以貼其左右兩側 viewport，並同時維持 article 當中文字受版心約束的設定，請問要如何調整css?謝謝

```html
<section id="home" class="hero">
                <picture>
                    <source media="(min-width: 768px)"
                        srcset="https://raw.githubusercontent.com/hexschool/2022-web-layout-training/refs/heads/main/week3-4/home-header.png">
                    <img src="https://raw.githubusercontent.com/hexschool/2022-web-layout-training/refs/heads/main/week3-4/home-header-sm.png"
                        alt="home reader">
                </picture>
                <article class="content">
                    <h1>Promise-Desert 2020 早春系列</h1>
                    <p>看得清，才能看得遠</p>
                    <button type="button" class="home-button">立即購買</button>
                </article>
            </section>
```

```css
@layer components{
  .hero {
    width: 100%;
    /* outline: auto; */
    overflow-x: hidden;
    position: relative;

    picture {
      width: 100%;
      display: block;

      img {
        width: 100%; /* 圖片寬度填滿容器 */
        height: auto; /* 高度按比例縮放 */
        object-fit: contain; /* 確保圖片完整顯示並保持比例 */
      }
    }

    .content {
      /* outline: auto; */
      width: 100%;
      position: absolute;
      top: 376px;
      right: 311px;
      text-align: right;

      & h1,
      & p,
      & button {
        /* outline: auto; */
        width: fit-content;
        text-align: center;
        max-width: 50%; /* 限制最大寬度，避免過長超出 */
        margin-left: auto; /* 靠右對齊 */
        margin-right: 0; /* 確保右邊無多餘間距 */
        letter-spacing: 0px;
        color: var(--primary-color);
        opacity: 1;
      }

      h1 {
        height: 54px;
        line-height: 54px;
        font-size: 36px;
      }

      p {
        height: 96px;
        line-height: 96px;
        font-size: 64px;
        margin-block-end: 10px;
      }

      button {
        height: 42px;
        font-size: 20px;
        margin-bottom: 10px;
        padding-inline: 12px;
        padding-block: 6px;
        background-color: var(--button-bg);
        color: #fff;
      }
    }
  }
}
```

1. 現在 picture 中的圖片沒有填滿 viewport 寬度，我需要他填滿 viewport
2. 填滿vieport 寬度後，我需要版心1296px 先置中 ，接著article 中的文字上下排列，文字靠版心右側貼整齊

請協助我調整 css，謝謝

