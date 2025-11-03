<template>
  <div id="app">
    <header class="header">
      <div class="logo">
        <img src="xx" alt="community-title" />
        <div class="community-title-container">
          <span class="main-community-title">北非业务运营中心</span>
          <span class="sub-community-title">知识共享，智领北非运营</span>
        </div>
      </div>

      <ul class="navigaotrsUl">
        <li v-for="item in navItems" :key="item" @click="toggleMegaMenu(item)">
          <a href="#">{{ item }}</a>
        </li>
      </ul>
      <span class="lang">EN</span>

      <div class="actions">
        <input type="text" placeholder="输入关键词搜索" />
      </div>
    </header>

    <div class="mega-menu" v-if="isMegaMenuOpen && activeMenu">
      <div class="mega-menu-content">
        <div class="menu-left">
          <h2>{{ menuData[activeMenu].title }}</h2>
          <p>{{ menuData[activeMenu].description }}</p>
        </div>
        <div class="menu-right">
          <div
            class="menu-column"
            v-for="(column, index) in menuData[activeMenu].columns"
            :key="index"
          >
            <h3>{{ column.title }}</h3>
            <ul>
              <li v-for="(link, linkIndex) in column.links" :key="linkIndex">
                <a href="#">{{ link }}</a>
              </li>
            </ul>
          </div>
        </div>
        <button class="close-menu" @click="toggleMegaMenu(activeMenu)">
          X
        </button>
      </div>
    </div>

    <main>
      <div class="main-content">
        <div class="banner-slider">
          <div
            v-for="(slide, index) in slides"
            :key="slide.id"
            class="slide"
            :class="{ 'active-slide': index === currentSlideIndex }"
            :style="{ backgroundImage: 'url(' + slide.url + ')' }"
          >
            <div class="slide-content">
              <div class="lines-container">
                <div
                  v-for="(line, lineIndex) in slides"
                  :key="line.id"
                  class="line"
                  :class="{ 'active-line': lineIndex === currentSlideIndex }"
                  :line-num="lineIndex + 1"
                  @click="goToSlide(lineIndex)"
                ></div>
              </div>
            </div>
          </div>
        </div>
        <div class="tabs">
          <ul>
            <li class="active"><a href="#">title1</a></li>
            <li><a href="#">title2</a></li>
            <li><a href="#">title3</a></li>
            <li><a href="#">title4</a></li>
            <li><a href="#">title5</a></li>
            <li><a href="#">title6</a></li>
            <li><a href="#">title7</a></li>
          </ul>
        </div>
        <div class="actions-bar">
          <button class="primary">推荐</button>
          <button>用户运营</button>
          <button>产品运营</button>
          <button>金融运营</button>
          <button>活动运营</button>
          <button>营销工具</button>
          <button>看板工具</button>
        </div>

        <div class="card-grid">
          <div class="card" v-for="n in 18" :key="n">
            <img :src="'xx'" alt="Card image" />
            <h3>2021云智技术论坛</h3>
            <p>作者名字</p>
          </div>
        </div>
      </div>
      <aside class="sidebar">
        <div class="user-profile">
          <img src="xx" alt="User avatar" />
          <h2>欢迎你 AIX A6015587</h2>
          <div class="stats">
            <div><span>168</span><span>贡献</span></div>
            <div><span>lv.2</span><span>贡献</span></div>
            <div><span>0</span><span>我关注</span></div>
            <div><span>0</span><span>关注我的</span></div>
          </div>
          <button>查看我的勋章</button>
        </div>
        <div class="ability-section">
          <h3>能力专项</h3>
          <div class="buttons">
            <button class="green"><span>☁️</span>云手机发布</button>
            <button class="blue"><span>🎮</span>游戏上线</button>
            <button class="green"><span>🎬</span>短剧上线</button>
            <button class="orange"><span>📖</span>阅读上线</button>
          </div>
        </div>
        <div class="learning-circle">
          <h3>学习圈子</h3>
          <div class="icons">
            <div><span>📄</span><span>白皮书</span></div>
            <div><span>👆</span><span>一指禅</span></div>
            <div><span>📁</span><span>产品文档</span></div>
          </div>
        </div>
        <div class="regional-star">
          <h3>地区部运营之星·5月</h3>
          <div class="user">
            <img src="xx" alt="User avatar" />
            <h4>李四 L12312</h4>
            <p>部门名称</p>
          </div>
        </div>
        <div class="hot-scenes">
          <h3>热门场景</h3>
          <ul>
            <li>
              <span>🔥</span>
              <div>
                <h4>营销活动</h4>
                <p>2025营销活动合集/营销活动介绍</p>
              </div>
            </li>
            <li>
              <span>🏆</span>
              <div>
                <h4>荣耀时刻</h4>
                <p>2025荣耀时刻合集/荣耀时刻介绍</p>
              </div>
            </li>
            <li>
              <span>🎉</span>
              <div>
                <h4>庆功表彰</h4>
                <p>2025庆功表彰合集/庆功表彰介绍</p>
              </div>
            </li>
          </ul>
        </div>
        <div class="monthly-report">
          <h3>运营月报·5月</h3>
          <ul>
            <li>title1</li>
            <li>title2</li>
            <li>title3</li>
          </ul>
        </div>
        <div class="honor-roll">
          <h3>社区月度荣誉榜单</h3>
          <ul>
            <li>
              <div class="rank second">2</div>
              <img src="xx" alt="User avatar" />
              <div>
                <h4>李四</h4>
                <p>LWX8958996</p>
              </div>
              <span>2000</span>
            </li>
            <li>
              <div class="rank first">1</div>
              <img src="xx" alt="User avatar" />
              <div>
                <h4>张三</h4>
                <p>ZWX88888888</p>
              </div>
              <span>3000</span>
            </li>
            <li>
              <div class="rank third">3</div>
              <img src="xx" alt="User avatar" />
              <div>
                <h4>王五</h4>
                <p>ZWX88888888</p>
              </div>
              <span>1000</span>
            </li>
            <li>
              <div class="rank">4</div>
              <img src="xx" alt="User avatar" />
              <div>
                <h4>Alex Zhang</h4>
              </div>
              <span>1000</span>
            </li>
            <li>
              <div class="rank">5</div>
              <img src="xx" alt="User avatar" />
              <div>
                <h4>Jack wang</h4>
              </div>
              <span>800</span>
            </li>
          </ul>
        </div>
        <div class="data-stats">
          <h3>数据统计</h3>
          <div class="stats-grid">
            <div><span>168</span><span>总访问数</span></div>
            <div><span>lv.2</span><span>当日访问量</span></div>
            <div><span>0</span><span>成员数</span></div>
            <div><span>0</span><span>新讨论数</span></div>
            <div><span>0</span><span>视频数</span></div>
          </div>
        </div>
        <div class="recent-visitors">
          <h3>最近访问列表</h3>
          <div class="visitors-grid">
            <div
              v-for="user in ['张三', '李四', '王五', 'Jack wang', 'Gottwald']"
              :key="user"
              class="visitor"
            >
              <img src="xx" alt="User avatar" />
              <span>{{ user }}</span>
            </div>
          </div>
        </div>
      </aside>
    </main>
    <footer>
      <p>footer | 联系我们</p>
      <p>Copyright © 2025. All Rights Reserved</p>
    </footer>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const navItems = [
  "新闻快讯",
  "运营领域",
  "融合运营",
  "专题精选",
  "荣誉专栏",
  "知识书架",
  "WIKI",
];

const menuData = {
  新闻快讯: {
    title: "新闻快讯",
    description: "这里是新闻快讯的描述，包含最新的公司动态和行业新闻。",
    columns: [
      { title: "今日头条", links: ["链接 1-1", "链接 1-2", "链接 1-3"] },
      { title: "行业动态", links: ["链接 2-1", "链接 2-2", "链接 2-3"] },
      { title: "公司新闻", links: ["链接 3-1", "链接 3-2", "链接 3-3"] },
    ],
  },
  运营领域: {
    title: "运营领域",
    description:
      "运营是通过一系列策略和执行，链接产品与用户，最终实现用户增长、留存和商业价值的核心职能。它并非单一岗位，而是一个覆盖多维度的体系化工作。",
    columns: [
      { title: "1", links: ["1", "2", "3", "4", "5", "6"] },
      { title: "2", links: ["1", "2", "3", "4", "5"] },
      { title: "3", links: ["1", "2", "3"] },
      { title: "4", links: ["1", "2", "3", "4"] },
      { title: "5", links: ["1", "2", "3", "4", "5", "6"] },
    ],
  },
  融合运营: {
    title: "融合运营",
    description: "融合运营的描述文本。",
    columns: [
      { title: "栏目A", links: ["链接 A-1", "链接 A-2"] },
      { title: "栏目B", links: ["链接 B-1", "链接 B-2"] },
    ],
  },
  专题精选: {
    title: "专题精选",
    description: "专题精选的描述文本。",
    columns: [
      { title: "专题1", links: ["文章1", "文章2", "文章3"] },
      { title: "专题2", links: ["文章A", "文章B", "文章C"] },
      { title: "专题3", links: ["文章X", "文章Y", "文章Z"] },
    ],
  },
  荣誉专栏: {
    title: "荣誉专栏",
    description: "荣誉专栏的描述文本。",
    columns: [
      { title: "个人荣誉", links: ["张三", "李四"] },
      { title: "团队荣誉", links: ["A-Team", "B-Team"] },
    ],
  },
  知识书架: {
    title: "知识书架",
    description: "知识书架的描述文本。",
    columns: [
      { title: "技术类", links: ["Vue.js", "React", "Angular"] },
      { title: "管理类", links: ["项目管理", "团队协作"] },
    ],
  },
  WIKI: {
    title: "WIKI",
    description: "WIKI的描述文本。",
    columns: [
      { title: "产品WIKI", links: ["产品A", "产品B"] },
      { title: "技术WIKI", links: ["前端", "后端"] },
    ],
  },
};

const isMegaMenuOpen = ref(false);
const activeMenu = ref(null);

const toggleMegaMenu = (item) => {
  if (activeMenu.value === item) {
    isMegaMenuOpen.value = false;
    activeMenu.value = null;
  } else {
    isMegaMenuOpen.value = true;
    activeMenu.value = item;
  }
};

// banner
const currentSlideIndex = ref(0);
const slides = ref([
  {
    id: 1,
    url: "xx",
  },
  {
    id: 2,
    url: "xx",
  },
  {
    id: 3,
    url: "xx",
  },
  {
    id: 4,
    url: "xx",
  },
  {
    id: 5,
    url: "xx",
  },
  {
    id: 6,
    url: "xx",
  },
]);

let slideInterval = null;
const nextSlide = () => {
  currentSlideIndex.value = (currentSlideIndex.value + 1) % slides.value.length;
};

// Function to handle clicking on a line
const goToSlide = (index) => {
  // Set the current slide to the one that was clicked
  currentSlideIndex.value = index;
  // Reset the auto-play timer
  clearInterval(slideInterval);
  slideInterval = setInterval(nextSlide, 3000);
};

// 3. LIFECYCLE
onMounted(() => {
  // Store the interval ID when we start it
  slideInterval = setInterval(nextSlide, 3000);
});

//  Clean up the interval when the component is removed
onUnmounted(() => {
  clearInterval(slideInterval);
});
</script>

<style scoped>
/* Global styles will go here */

body {
  margin: 0;
  background-color: #f5f5f5;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 0px;
  background-color: white;
  border-bottom: 1px solid #eaeaea;
  width: 80vw;
  margin-inline: auto;
  gap: 3vw;
}

.logo {
  display: flex;
  align-items: center;
  gap: 1vw;
}

.logo img {
  height: 50px;
  width: 50px;
  border-radius: 50%;
}
.community-title-container {
  display: flex;
  flex-direction: column;
}
.main-community-title {
  font-size: 17px;
  font-weight: bold;
}
.sub-community-title {
  font-size: 14px;
}

.navigaotrsUl {
  list-style: none;
  display: flex;
  margin: 0;
  padding: 0;
  gap: 1vw;
  width: 37.5vw;
}

.navigaotrsUl li a {
  text-decoration: none;
  color: #333;
  /* font-weight: bold; */
}

.actions {
  display: flex;
  align-items: center;
}

.actions a {
  margin-right: 15px;
  text-decoration: none;
  color: #333;
}

.actions input {
  border: 1px solid #ccc;
  padding: 8px;
  border-radius: 5px;
}

main {
  display: flex;
  padding: 20px 0px;
  width: 80vw;
  margin-inline: auto;
}

.main-content {
  flex: 3;
  margin-right: 20px;
}
.banner-slider {
  position: relative;
  width: 100%;
  height: 13vw;
  overflow: hidden;
}

.slide {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  opacity: 0;
  transition: opacity 0.5s ease-in-out;
  cursor: pointer;
}

.active-slide {
  opacity: 1;
}

.slide-content {
  position: relative;
  width: 100%;
  height: 100%;
}

.lines-container {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 10px;
  z-index: 10;
}

.line {
  width: 30px;
  height: 4px;
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 2px;
  transition: background-color 0.3s;
  /* NEW: Add cursor pointer to show it's clickable */
  cursor: pointer;
}

.active-line {
  background-color: white;
}

.tabs ul {
  list-style: none;
  display: flex;
  padding: 0;
  border-bottom: 2px solid #ccc;
}

.tabs li {
  margin-right: 30px;
  padding-bottom: 10px;
  cursor: pointer;
}

.tabs li.active {
  border-bottom: 2px solid #007bff;
  color: #007bff;
}

.actions-bar {
  margin: 20px 0;
}

.actions-bar button {
  border: 1px solid #ccc;
  background-color: white;
  padding: 10px 20px;
  border-radius: 20px;
  margin-right: 10px;
  cursor: pointer;
}

.actions-bar button.primary {
  background-color: #007bff;
  color: white;
  border: none;
}

.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 20px;
}

.card {
  background-color: white;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.card img {
  width: 100%;
}

.card h3 {
  font-size: 16px;
  margin: 10px;
}

.card p {
  font-size: 14px;
  color: #888;
  margin: 10px;
}

.sidebar {
  flex: 1;
}

.sidebar > div {
  background-color: white;
  padding: 20px;
  border-radius: 10px;
  margin-bottom: 20px;
}

.user-profile {
  text-align: center;
}

.user-profile img {
  width: 80px;
  height: 80px;
  border-radius: 50%;
}

.user-profile h2 {
  font-size: 18px;
  margin: 10px 0;
}

.user-profile .stats {
  display: flex;
  justify-content: space-around;
  margin: 20px 0;
}

.user-profile .stats div {
  display: flex;
  flex-direction: column;
}

.user-profile .stats span:first-child {
  font-size: 18px;
  font-weight: bold;
}

.user-profile button {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 20px;
  cursor: pointer;
  width: 100%;
}

.ability-section .buttons {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
}

.ability-section button {
  border: none;
  padding: 10px;
  border-radius: 5px;
  color: white;
  cursor: pointer;
}

.ability-section .green {
  background-color: #28a745;
}
.ability-section .blue {
  background-color: #007bff;
}
.ability-section .orange {
  background-color: #fd7e14;
}

.learning-circle .icons {
  display: flex;
  justify-content: space-around;
  text-align: center;
}

.regional-star .user {
  text-align: center;
}

.regional-star img {
  width: 60px;
  height: 60px;
  border-radius: 50%;
}

.hot-scenes ul,
.monthly-report ul,
.honor-roll ul {
  list-style: none;
  padding: 0;
}

.hot-scenes li,
.monthly-report li,
.honor-roll li {
  display: flex;
  align-items: center;
  margin-bottom: 15px;
}

.hot-scenes span {
  font-size: 24px;
  margin-right: 15px;
}

.honor-roll .rank {
  font-size: 18px;
  font-weight: bold;
  width: 30px;
  height: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  color: white;
  margin-right: 15px;
}

.honor-roll .rank.first {
  background-color: #ffd700;
}
.honor-roll .rank.second {
  background-color: #c0c0c0;
}
.honor-roll .rank.third {
  background-color: #cd7f32;
}

.honor-roll img {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  margin-right: 15px;
}

.honor-roll span {
  margin-left: auto;
  font-weight: bold;
}

.data-stats .stats-grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 20px;
  text-align: center;
}

.data-stats .stats-grid div {
  display: flex;
  flex-direction: column;
}

.recent-visitors .visitors-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(60px, 1fr));
  gap: 15px;
  text-align: center;
}

.recent-visitors .visitor img {
  width: 50px;
  height: 50px;
  border-radius: 50%;
}

footer {
  text-align: center;
  padding: 20px;
  background-color: #007bff;
  color: white;
}

.mega-menu {
  position: absolute;
  top: 70px; /* Adjust this based on your header's height */
  left: 0;
  width: 100%;
  background-color: white;
  border-top: 1px solid #eaeaea;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  z-index: 1000;
}

.mega-menu-content {
  display: flex;
  justify-content: space-between;
  padding: 40px 100px;
  max-width: 1200px;
  margin: 0 auto;
}

.menu-left {
  flex-basis: 25%;
  padding-right: 40px;
}

.menu-left h2 {
  font-size: 24px;
  margin-bottom: 20px;
}

.menu-right {
  flex-basis: 75%;
  display: flex;
  justify-content: space-between;
}

.menu-column {
  flex: 1;
  padding: 0 20px;
}

.menu-column h3 {
  font-size: 18px;
  margin-bottom: 20px;
  border-bottom: 1px solid #eaeaea;
  padding-bottom: 10px;
}

.menu-column ul {
  list-style: none;
  padding: 0;
}

.menu-column li {
  margin-bottom: 15px;
}

.menu-column a {
  text-decoration: none;
  color: #333;
}

.close-menu {
  position: absolute;
  top: 20px;
  right: 20px;
  background: none;
  border: none;
  font-size: 24px;
  cursor: pointer;
}
</style>
