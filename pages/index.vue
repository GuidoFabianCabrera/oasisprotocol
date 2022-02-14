<template>
  <div>
    <div class="main">
      <section class="nav">
        <div class="nav__container custom_container">
          <img class="nav__logo" src="images/oasis.svg" alt="nav logo" />
          <v-icon class="nav__icon">mdi-menu</v-icon>
          <div class="nav__menu">
            <v-menu
              open-on-hover
              offset-y
              v-for="(item, index) in nav"
              :key="index"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-btn
                  text
                  x-large
                  v-bind="attrs"
                  v-on="on"
                  class="nav__menu_item"
                >
                  {{ item.title }} <v-icon>mdi-chevron-down</v-icon>
                </v-btn>
              </template>

              <v-list light>
                <v-list-item
                  color="success"
                  v-for="(item, index) in item.links"
                  :key="index"
                >
                  <v-list-item-title>{{ item }}</v-list-item-title>
                </v-list-item>
              </v-list>
            </v-menu>
          </div>
        </div>
      </section>

      <section class="hero">
        <div class="hero__container custom_container ">
          <div class="hero__left">
            <h1 class="hero__title">A new era for blockchain</h1>
            <p class="hero__description">
              The Oasis Network is a privacy-enabled blockchain platform for
              open finance and a responsible data economy.
            </p>
            <v-btn class="hero__button" light elevation="2" rounded small
              >Watch Video <v-icon>mdi-chevron-right</v-icon>
            </v-btn>
          </div>
          <div class="hero__right">
            <img class="hero__image" src="images/hero.svg" alt="hero image" />
          </div>
        </div>
        <img
          class="hero__separator"
          src="images/separator.svg"
          alt="separator"
        />
      </section>
    </div>

    <section class="involved">
      <div class="involved__container custom_container custom_container--lg">
        <h1 class="involved__title">Get Involved</h1>
        <div class="involved__list">
          <div
            class="card_involved"
            v-for="(item, index) in involved"
            :key="index"
          >
            <div class="card_involved__logo">
              <img v-bind:src="item.logo" v-bind:alt="item.logo" />
            </div>
            <div class="card_involved__title" v-html="item.title"></div>
            <div class="card_involved__link">
              Get Started
              <v-icon class="card_involved__arrow">mdi-arrow-right</v-icon>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="meet_oasis">
      <div class="meet_oasis__container custom_container custom_container--lg">
        <h1 class="meet_oasis__title">Meet the Oasis Network</h1>

        <div class="meet_oasis__list">
          <div class="card_meet" v-for="(item, index) in meet" :key="index">
            <img
              class="card_involved__logo"
              v-bind:src="item.logo"
              v-bind:alt="item.logo"
            />
            <h4 class="card_meet__title">{{ item.title }}</h4>
            <div class="card_meet__description">{{ item.description }}</div>
            <v-btn color="#0092f6" rounded small
              >Learn more <v-icon>mdi-chevron-right</v-icon></v-btn
            >
          </div>
        </div>
      </div>
    </section>

    <section class="highlights">
      <div class="highlights__separatorTop"></div>
      <div class="highlights__container custom_container custom_container--lg">
        <h1 class="highlights__title">Technology Highlights</h1>
        <v-btn color="#0092f6" rounded small class="highlights__button"
          >Learn more <v-icon>mdi-chevron-right</v-icon></v-btn
        >

        <div class="highlights__list">
          <div
            class="card_meet"
            v-for="(item, index) in highlights"
            :key="index"
            @mouseover="highlights_image = item.image"
          >
            <img
              class="card_involved__logo"
              v-bind:src="item.logo"
              v-bind:alt="item.logo"
            />
            <h4 class="card_meet__title">{{ item.title }}</h4>
            <div class="card_meet__description">{{ item.description }}</div>
          </div>
          <img class="highlights__image" v-bind:src="highlights_image" />
        </div>
      </div>
      <div class="highlights__separatorBottom"></div>
    </section>

    <section class="community">
      <div class="community__container custom_container custom_container--lg">
        <h1 class="community__title">Rapidly Growing Community</h1>
        <p class="community__description">
          The Oasis Network has a thriving community of close to a thousand node
          operators, developers, enterprise partners, ambassadors, and nearly
          ten thousand community members engaged in global social channels. We’d
          love to have you onboard.
        </p>
        <p class="community__telegram">
          Join our <strong>Telegram channel</strong> to learn more.
        </p>
        <v-btn color="#0092f6" rounded small class="community__button"
          >Join Telegram <v-icon>mdi-chevron-right</v-icon></v-btn
        >
      </div>
    </section>

    <section class="news">
      <div class="news__separatorTop"></div>

      <div class="news__container custom_container custom_container--lg ">
        <h2 class="news__title">News</h2>
        <v-btn color="#161c3d" rounded class="news__button"
          >Read more on our Medium <v-icon>mdi-chevron-right</v-icon></v-btn
        >
        <div class="news__list">
          <div
            class="card_news"
            v-for="(item, index) in news"
            :key="index"
            v-bind:style="{ background: item.background }"
          >
            <h4 class="card_news__title">{{ item.title }}</h4>
            <div class="card_news__description">{{ item.description }}</div>
            <div class="card_news__link">
              Read More <v-icon>mdi-chevron-right</v-icon>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="partners">
      <div class="partners__container custom_container custom_container--lg">
        <h2 class="partners__title">Partners</h2>
        <div class="partners__list">
          <div
            class="card_partners"
            v-for="(item, index) in partners"
            :key="index"
          >
            <h4 class="card_partners__title">
              {{ item.title
              }}<span class="card_partners__link"
                >See more
                <v-icon class="card_partners__icon"
                  >mdi-chevron-right</v-icon
                ></span
              >
            </h4>
            <div class="card_partners__list">
              <div
                class="card_partners__image_container"
                v-for="(item, index) in item.images"
                :key="index"
                :class="{ 'card_partners__image_container--small': item.small }"
              >
                <img class="card_partners__image" v-bind:src="item.url" />
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <footer class="footer">
      <div class="footer__container custom_container custom_container--lg">
        <div class="footer__form_container">
          <img class="footer__image" src="images/footer.svg" alt="footer" />
          <p class="footer__input_text">Register for the Newsletter:</p>
          <input
            class="footer__input"
            type="text"
            placeholder="Email Address"
          />
          <v-btn color="#0092f6" rounded>Submit</v-btn>
        </div>
        <div class="footer__list">
          <div class="footer__list_title">TECHNOLOGY</div>
          <div class="footer__list_item">Primer</div>
          <div class="footer__list_item">Tech overview</div>
          <div class="footer__list_item">Security</div>
          <div class="footer__list_item">Wallets</div>
        </div>
        <div class="footer__list">
          <div class="footer__list_title">DEVELOPERS</div>
          <div class="footer__list_item">Documentation</div>
          <div class="footer__list_item">Github</div>
        </div>
        <div class="footer__list">
          <div class="footer__list_title">COMMUNITY</div>
          <div class="footer__list_item">Careers</div>
          <div class="footer__list_item">Telegram</div>
          <div class="footer__list_item">Slack</div>
          <div class="footer__list_item">Medium blog</div>
          <div class="footer__list_item">Partners</div>
        </div>
        <div class="footer__social">
          <img class="footer__social_icon" src="images/social_telegram.svg" />
          <img class="footer__social_icon" src="images/social_slack.svg" />
          <img class="footer__social_icon" src="images/social_twitter.svg" />
          <img class="footer__social_icon" src="images/social_github.svg" />
          <img class="footer__social_icon" src="images/social_youtube.svg" />
          <img class="footer__social_icon" src="images/social_oasis.svg" />
          <img class="footer__social_icon" src="images/social_discord.png" />
        </div>
        <div class="footer__legal">
          <div class="footer__legal_item">Terms of Use</div>
          <div class="footer__legal_item">Privacy Policy</div>
          <div class="footer__legal_item">
            Copyright © 2021 Oasis Protocol Foundation. All rights reserved.
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nav: [
        {
          title: "TECHNOLOGY",
          links: [
            "Overview",
            "Developer Portal",
            "Primer",
            "Papers",
            "Documentation",
            "Github",
            "Rose Token",
            "Wallets"
          ]
        },
        {
          title: "GET INVOLVED",
          links: [
            "Join our Telegram",
            "Apply for a Grant",
            "Ecosystem Fund",
            "Oasis Accelerator",
            "Become an Ambassador",
            "University Program",
            "Run a Node",
            "YuzuSwap Dex"
          ]
        },
        {
          title: "COMMUNITY",
          links: [
            "Community",
            "Partners",
            "Telegram (Community discussion)",
            "Slack channel (Dev support)",
            "Blog",
            "Twitter",
            "Team"
          ]
        }
      ],
      involved: [
        {
          logo: "images/telegram.svg",
          title: "Join our <strong>Telegram</strong>"
        },
        {
          logo: "images/building.svg",
          title: "Start <strong>Building</strong>"
        },
        {
          logo: "images/grant.svg",
          title: "Apply for <strong>Grant</strong>"
        },
        {
          logo: "images/ambassador.svg",
          title: "Be an <strong>Ambassador</strong>"
        },
        {
          logo: "images/node.svg",
          title: "Run a <strong>Node</strong>"
        }
      ],
      meet: [
        {
          title: "Private and Scalable DeFi",
          description:
            "By bringing privacy and scalability to DeFi, the Oasis Network expands DeFi beyond early adopters to a mass market. It enables private smart contracts, high scalability, and the ability to tokenize data. This unlocks new use cases like private lending, undercollateralized loans, and private automated market makers.",
          logo: "images/private.svg"
        },
        {
          title: "Tokenizing Data",
          description:
            "The Oasis Network’s unique combination of confidential computing and blockchain enables a new paradigm called Tokenized Data. With Tokenized Data users can earn rewards by staking their data with apps that want to analyze it or control how their most sensitive information is consumed by the services they use.",
          logo: "images/token.svg"
        },
        {
          title: "Parallel Smart Contract Layers",
          description:
            "The Oasis ParaTime scaling architecture supports fast transaction speed, high scalability, and large workloads by separating execution from consensus. Anyone can create their own ParaTime, allowing for the Oasis Network to support a rich ecosystem of applications and use cases.",
          logo: "images/contract.svg"
        }
      ],
      highlights: [
        {
          title: "Scalable, Reliable and Versatile",
          description:
            "The Oasis Network separates consensus and execution into two layers — the Consensus Layer and The ParaTime Layer — for better scalability and increased versatility.",
          logo: "images/scalable.svg",
          image: "images/scalable-image.svg"
        },
        {
          title: "Parallel Workloads",
          description:
            "Separation of consensus and execution allows multiple ParaTimes to process transactions in parallel, meaning complex workloads processed on one ParaTime won’t slow down faster, simpler transactions on another.",
          logo: "images/parallel.svg",
          image: "images/parallel-image.svg"
        },
        {
          title: "Confidential Smart Contracts",
          description:
            "The first network to support confidential smart contracts. The Oasis Eth/WASI Runtime is an open source example of a confidential ParaTime that uses secure enclaves to keep data private while being processed.",
          logo: "images/confidential.svg",
          image: "images/confidential-image.svg"
        },
        {
          title: "Efficient Design",
          description:
            "The network’s unique system of discrepancy detection makes Oasis more efficient than sharding and parachains — requiring a smaller replication factor for the same level of security.",
          logo: "images/efficient.svg",
          image: "images/efficient-image.svg"
        }
      ],
      highlights_image: "images/scalable-image.svg",
      news: [
        {
          title:
            "Oasis Mainnet: Ushering in a New Era of Privacy and Scalability",
          description:
            "The Oasis Mainnet launch is the start of a new era of scalable, private blockchain networks that can revolutionize DeFi and tokenize data.",
          background: "#0092f6"
        },
        {
          title: "6,700 New Token Holders Join Oasis on CoinList",
          description:
            "We’re excited to announce that the Oasis Network’s novel farming and staking program, the ROSE Garden on CoinList, has added more than 6,700 new Oasis token holders to the network in just three weeks.",
          background: "#0054f6"
        },
        {
          title:
            "The Oasis Network joins the BSN Platform Alongside Polkadot and Bityuan",
          description:
            "BSN’s addition of the Oasis Network unlocks a new privacy-enabled blockchain for China’s developers.",
          background: "#7c3fca"
        }
      ],
      partners: [
        {
          title: "Node Operators",
          images: [
            { url: "images/operators-1.png", small: false },
            { url: "images/operators-2.png", small: false },
            { url: "images/operators-3.png", small: false },
            { url: "images/operators-4.png", small: false }
          ]
        },
        {
          title: "Developers",
          images: [
            { url: "images/developers-1.png", small: false },
            { url: "images/developers-2.png", small: false },
            { url: "images/developers-3.png", small: false },
            { url: "images/developers-4.png", small: false }
          ]
        },
        {
          title: "Select Backers",
          images: [
            { url: "images/backers-1.png", small: true },
            { url: "images/backers-2.png", small: true },
            { url: "images/backers-3.png", small: false },
            { url: "images/backers-4.png", small: false }
          ]
        }
      ]
    };
  }
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/utils";
.v-btn {
  text-transform: unset !important;
  font-size: 14px;
}

.main {
  // height: 100vh;
  background-image: linear-gradient(149deg, #0092f6, #3552eb);
}

.nav {
  .nav__container {
    // height: 70px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-top: 20px;
    padding-bottom: 20px;
  }

  .nav__logo {
    width: 192px;
    height: 19px;
    @include breakpoint(sm) {
      width: 240px;
      height: 24px;
    }
  }

  .nav__icon {
    @include breakpoint(lg) {
      display: none;
    }
  }

  .nav__menu {
    display: none;
    @include breakpoint(lg) {
      display: flex;
      align-items: center;
    }
  }

  .nav__menu_item {
    font-size: 15px;
    font-weight: 700;
    letter-spacing: 1px;
  }
}

.hero {
  position: relative;

  .hero__container {
    padding-bottom: 100px;
    margin-top: 35px;
    @include breakpoint(sm) {
      display: flex;
      align-items: center;
      padding-bottom: 150px;
    }
    @include breakpoint(md) {
      padding-bottom: 220px;
    }
  }

  .hero__left {
    padding-bottom: 24px;
    @include breakpoint(sm) {
      padding-bottom: 0;
      padding-right: 7vw;
      max-width: 50%;
    }
  }

  .hero__title {
    padding-bottom: 24px;
    font-size: 44px;
    line-height: 49px;
    letter-spacing: -1.5px;
    @include breakpoint(sm) {
      font-size: 57px;
      line-height: 67px;
    }
    @include breakpoint(lg) {
      font-size: 6vw;
      line-height: 6.5vw;
    }
    @include breakpoint(xl) {
      // font-size: 79px;
    }
  }

  .hero__description {
    margin-bottom: 0;
    padding-bottom: 24px;
    font-size: 16px;
    line-height: 22px;
    font-weight: 400;
    @include breakpoint(lg) {
      padding-bottom: 40px;
      font-size: 17px;
    }
  }

  .hero__button {
    color: #0092f6;
    font-weight: 700;
    letter-spacing: 0px;
    text-transform: capitalize;
    font-size: 14px;
  }

  .hero__right {
    padding-top: 24px;
    @include breakpoint(sm) {
      padding-top: 0;
      width: 100%;
      max-width: 50%;
    }
  }

  .hero__image {
    width: 100%;
  }

  .hero__separator {
    position: absolute;
    left: 0;
    bottom: -1px;
    width: 100%;
  }
}

.involved {
  background-color: #f7f9fc;

  .involved__container {
    padding-top: 50px;
    padding-bottom: 50px;
  }

  .involved__title {
    font-size: 28px;
    color: #243f5f;
    margin-bottom: 30px;
    @include breakpoint(sm) {
      font-size: 34px;
    }
  }

  .involved__list {
    display: flex;
    flex-wrap: wrap;
    column-gap: 10px;

    @include breakpoint(sm) {
      justify-content: space-around;
    }
    @include breakpoint(lg) {
      flex-wrap: nowrap;
    }
  }
}

.card_involved {
  border-radius: 4px;
  margin-bottom: 10px;
  padding: 15px;

  &:hover {
    @include breakpoint(lg) {
      background-color: rgb(229, 239, 255);
    }
  }
  @include breakpoint(lg) {
    width: 100%;
  }

  .card_involved__logo {
    width: 40px;
    margin-bottom: 3px;
  }

  .card_involved__title {
    color: #243f5f;
    margin-bottom: 7px;
  }

  .card_involved__link {
    color: #0092f6;
    font-weight: 500;
  }

  .card_involved__arrow {
    color: #0092f6;
  }
}

.meet_oasis {
  background-color: white;

  .meet_oasis__container {
    padding-top: 50px;
    padding-bottom: 50px;
    color: #243f5f;
  }

  .meet_oasis__title {
    font-size: 28px;
    margin-bottom: 30px;
    @include breakpoint(sm) {
      font-size: 34px;
    }
  }

  .meet_oasis__list {
    display: grid;
    column-gap: 20px;
    row-gap: 50px;
    @include breakpoint(sm) {
      grid-template-columns: repeat(2, auto);
    }
    @include breakpoint(md) {
      grid-template-columns: repeat(3, auto);
    }
  }
}

.card_meet {
  // border: 1px solid red;

  .card_meet__title {
    margin-bottom: 10px;
    @include breakpoint(lg) {
      font-size: 20px;
    }
  }

  .card_meet__description {
    margin-bottom: 15px;
    font-size: 15px;
    @include breakpoint(lg) {
      font-size: 16px;
    }
  }
}

.highlights {
  background-color: #161c3d;

  .highlights__container {
    padding-top: 50px;
    padding-bottom: 50px;
    color: white;
  }

  .highlights__separatorTop {
    height: 200px;
    margin-top: -60px;
    background-color: #161c3d;
    background-image: linear-gradient(176deg, #fff 64%, #161c3d 0);
  }

  .highlights__separatorBottom {
    height: 200px;
    background-color: #161c3d;
    background-image: linear-gradient(176deg, #161c3d 56%, #fff 0);
  }

  .highlights__title {
    font-size: 28px;
    margin-bottom: 15px;
    @include breakpoint(sm) {
      font-size: 34px;
    }
  }

  .highlights__button {
    margin-bottom: 40px;
  }

  .highlights__list {
    display: grid;
    column-gap: 20px;
    row-gap: 50px;
    @include breakpoint(md) {
      grid-template-columns: repeat(2, auto);
    }
    @include breakpoint(lg) {
      grid-template-columns: repeat(3, auto);
    }
  }

  .highlights__image {
    display: none;
    @include breakpoint(lg) {
      width: 306.672px;
      display: block;
      align-self: center;
      grid-column: 3 / 4;
      grid-row: 1 / 3;
    }
  }
}

.community {
  background-color: white;
  color: #243f5f;

  .community__container {
    display: flex;
    flex-direction: column;
    row-gap: 15px;

    @include breakpoint(sm) {
      padding-top: 60px;
      display: grid;
      grid-template-columns: 1.4fr 1fr;
      column-gap: 25px;
      row-gap: 0;
      grid-template-areas:
        "title title"
        "description telegram"
        "description button";
    }
  }

  .community__title {
    grid-area: title;
    font-size: 28px;
    @include breakpoint(sm) {
      font-size: 34px;
      margin-bottom: 30px;
    }
  }

  .community__description {
    grid-area: description;
  }

  .community__telegram {
    grid-area: telegram;
    @include breakpoint(sm) {
      margin-bottom: 0px;
    }
  }

  .community__button {
    width: fit-content;
    grid-area: button;
  }
}

.news {
  background-color: #f7f9fc;
  color: #243f5f;

  .news__separatorTop {
    height: 100px;
    background-image: linear-gradient(176deg, #fff 49%, #f7f9fc 0);
    @include breakpoint(sm) {
      height: 230px;
    }
  }

  .news__container {
    padding-bottom: 60px;
  }

  .news__title {
    font-size: 28px;
    @include breakpoint(sm) {
      font-size: 34px;
    }
  }

  .news__button {
    margin-top: 20px;
  }

  .news__list {
    margin-top: 20px;
    @include breakpoint(sm) {
      display: grid;
      grid-template-columns: repeat(2, auto);
      column-gap: 16px;
      margin-top: 40px;
    }
    @include breakpoint(lg) {
      grid-template-columns: repeat(3, auto);
    }
  }
}

.card_news {
  color: white;
  padding: 12px 16px;
  border-radius: 10px;
  margin-bottom: 20px;
  display: flex;
  flex-direction: column;
  row-gap: 12px;
  box-shadow: 1px 1px 20px 2px rgb(16 28 60 / 20%);
  transition: transform 0.15s ease;

  @include breakpoint(sm) {
    padding: 30px 20px;
  }

  &:hover {
    @include breakpoint(lg) {
      transform: scale(1.04);
    }
  }

  .card_news__title {
    font-size: 16px;
    @include breakpoint(sm) {
      font-size: 20px;
    }
  }

  .card_news__description {
    font-size: 14px;
    @include breakpoint(sm) {
      font-size: 16px;
    }
  }

  .card_news__link {
    font-size: 14px;
  }
}

.partners {
  background: white;

  .partners__container {
    padding-top: 40px;
    padding-bottom: 40px;
    color: #243f5f;
    @include breakpoint(sm) {
      padding-top: 60px;
      padding-bottom: 60px;
    }
  }

  .partners__title {
    font-size: 28px;
    @include breakpoint(sm) {
      font-size: 34px;
    }
  }

  .partners__list {
    margin-top: 20px;
    display: flex;
    flex-direction: column;
    row-gap: 50px;
  }
}

.card_partners {
  .card_partners__title {
    font-size: 24px;
    font-weight: 400;
    display: grid;
    grid-template-columns: 1fr 0.9fr;
    align-items: center;
    @include breakpoint(sm) {
      grid-template-columns: 0.8fr 1fr;
    }
    @include breakpoint(md) {
      grid-template-columns: 0.7fr 1fr;
    }
    @include breakpoint(lg) {
      grid-template-columns: 0.5fr 1fr;
    }
  }

  .card_partners__link {
    font-size: 14px;
    color: #0092f6;
    font-weight: 500;
  }

  .card_partners__icon {
    vertical-align: middle;
    color: #0092f6;
  }

  .card_partners__list {
    border: 1px solid #e6e9ec;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    column-gap: 25px;
    align-items: center;
    padding: 15px 10px;
    @include breakpoint(md) {
      border: none;
      column-gap: 55px;
    }
  }

  .card_partners__image_container--small {
    @include breakpoint(sm) {
      padding-right: 35px;
      padding-left: 35px;
    }
    @include breakpoint(md) {
      padding-right: 48px;
      padding-left: 48px;
    }
  }

  .card_partners__image {
    width: 100%;
    vertical-align: middle;
    max-height: 80px;
    object-fit: contain;
  }
}

.footer {
  background-color: #eaf0f4;
  color: black;
  padding-top: 30px;
  padding-bottom: 30px;

  @include breakpoint(md) {
    padding-top: 60px;
    padding-bottom: 60px;
  }

  .footer__container {
    display: flex;
    flex-wrap: wrap;
    // justify-content: space-between;
    // column-gap: 40px;
    @include breakpoint(sm) {
      justify-content: space-between;
    }
  }

  .footer__form_container {
    width: 100%;
    margin-bottom: 35px;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    @include breakpoint(md) {
      width: initial;
      min-width: 300px;
    }
  }

  .footer__image {
    max-height: 32px;
    margin-bottom: 50px;
    width: 100%;
    @include breakpoint(sm) {
      width: initial;
    }
  }

  .footer__input_text {
    font-size: 16px;
    color: #98a1ad;
    @include breakpoint(lg) {
      font-size: 11px;
    }
  }

  .footer__input {
    width: 100%;
    height: 38px;
    padding: 8px 12px;
    margin-bottom: 10px;
    font-size: 14px;
    line-height: 1.42857143;
    color: #333333;
    vertical-align: middle;
    background-color: #ffffff;
    border: 1px solid #cccccc;
    @include breakpoint(sm) {
      width: 50%;
    }
    @include breakpoint(md) {
      width: 100%;
    }
  }

  .footer__list {
    min-width: 50%;
    margin-bottom: 50px;
    @include breakpoint(sm) {
      min-width: 29%;
    }
    @include breakpoint(sm) {
      min-width: 0;
    }
  }

  .footer__list_title {
    margin-bottom: 25px;
    color: #8893a2;
    font-size: 14px;
    line-height: 1.5;
    font-weight: 700;
    letter-spacing: 1px;
  }

  .footer__list_item {
    font-size: 14px;
    color: #98a1ad;
    font-weight: 400;
    margin-bottom: 20px;
    @include breakpoint(lg) {
      font-size: 11px;
    }
  }

  .footer__social {
    width: 100%;
    display: none;
    @include breakpoint(md) {
      display: block;
      padding-bottom: 50px;
    }
  }

  .footer__social_icon {
    width: 42px;
    margin-right: 15px;
    vertical-align: middle;
    cursor: pointer;
    @include breakpoint(lg) {
      margin-right: 40px;
    }
  }

  .footer__legal {
    width: 100%;
    display: flex;
    flex-direction: column;
    padding-top: 15px;
    border-top: 1px solid #dfe1e5;
    color: #98a1ad;
    @include breakpoint(lg) {
      flex-direction: row;
      justify-content: space-between;
    }
  }

  .footer__legal_item {
    font-size: 12.5px;
    line-height: 23px;
    text-align: left;
    @include breakpoint(lg) {
      font-size: 11px;
    }
  }
}
</style>
