<template>
    <div class="profile-container">
        <article class="section-info">
            <div class="row">
                <div class="col info">
                    <p>
                        <span>ชื่อ:</span>รณชัย มะโนปา
                    </p>
                    <p>
                        <span>ชื่อเล่น:</span>ดุ่ย
                    </p>
                    <p>
                        <span>อายุ:</span>
                        {{ new Date().getFullYear() - 1988 }} ปี
                    </p>
                    <p>
                        <span>ภูมิลำเนา:</span>อุตรดิตถ์
                    </p>
                    <p>
                        <span>การศึกษา:</span>
                        <span class="right">
                            <span>วศ.บ วิศวกรรมคอมพิวเตอร์</span>
                            <span>มหาวิทยาลัยราชภัฏอุตรดิตถ์</span>
                        </span>
                    </p>
                    <p>
                        <span>อีเมล:</span>
                        <span>uttdev@gmail.com</span>
                    </p>
                    <p>
                        <span>เบอร์โทร:</span>
                        <span>0802324586</span>
                    </p>
                </div>
                <div class="col profile">
                    <img
                        class="profile-img"
                        src="@/images/profile.png"
                        alt="Ronnachai Manopa"
                        loading="lazy"
                    />
                </div>
            </div>
        </article>
        <article class="section-career card">
            <header>
                <h2>ประสบการณ์การทำงาน / Career Experience</h2>
            </header>
            <div>
                <p class="row">
                    <span>พ.ศ. 2556 - พ.ศ. 2563</span>
                    <span>ตำแหน่งโปรแกรมเมอร์ บริษัทออลล์เว็บเทคโนโลยี่ จำกัด</span>
                </p>
                <p class="row">
                    <span>พ.ศ. 2563 - ปัจจุบัน</span>
                    <span>โปรแกรมเมอร์อิสระ</span>
                </p>
            </div>
        </article>
        <article class="section-skill card">
            <header>
                <h2>ทักษะทางด้านโปรแกรมมิ่ง / Programming skills</h2>
            </header>
            <div class="skills">
                <div class="skill-container" title="Node.JS">
                    <img src="@/images/node.png" />
                    <process-bar :per="100" color="#8BC500"></process-bar>
                </div>
                <div class="skill-container" title="React.JS, React Native, Next.JS">
                    <img src="@/images/react.png" />
                    <process-bar :per="100" color="#47D8FF"></process-bar>
                </div>
                <div class="skill-container" title="Vue.JS, Nuxt.JS">
                    <img src="@/images/vue.png" />
                    <process-bar :per="100" color="#41B883"></process-bar>
                </div>
                <div class="skill-container" title="Wordpress">
                    <img src="@/images/wordpress.png" />
                    <process-bar :per="100" color="#32373C"></process-bar>
                </div>
                <div class="skill-container" title="Codeigniter">
                    <img src="@/images/codeigniter.png" />
                    <process-bar :per="100" color="#EE4323"></process-bar>
                </div>
                <div class="skill-container" title="Laravel">
                    <img src="@/images/laravel.png" />
                    <process-bar :per="80" color="#F52D22"></process-bar>
                </div>
                <div class="skill-container" title="Flutter">
                    <img src="@/images/flutter.png" />
                    <process-bar :per="50" color="#54C5F8"></process-bar>
                </div>
            </div>
        </article>
        <article class="section-workings card">
            <header>
                <h2>ผลงาน / Workings</h2>
            </header>
            <div class="works">
                <a href="https://framepersec.com/" target="_blank">
                    <img src="@/images/framepersec.png" loading="lazy" />
                </a>
                <a href="https://allweb.co.th/2019/" target="_blank">
                    <img src="@/images/allweb.png" loading="lazy" />
                </a>
                <a href="https://www.booking-ticket.com/" target="_blank">
                    <img src="@/images/booking.png" loading="lazy" />
                </a>
                <a href="https://www.ticket-fd.com/" target="_blank">
                    <img src="@/images/fd.png" loading="lazy" />
                </a>
            </div>
        </article>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import ProcessBar from '@/components/ProcessBar.vue'

export default defineComponent({
    components: {
        ProcessBar
    }
})
</script>

<style scoped>
.profile-container {
    padding: 1rem;
}
.row {
    display: flex;
    flex-direction: row;
}

.row {
    align-items: center;
    justify-content: space-between;
}

.card {
    padding: 1rem;
    margin-bottom: 2rem;
    box-shadow: 0 0 16px rgba(0, 0, 0, 0.2);
    border-radius: 12px;
    background-color: rgba(255, 255, 255, 0.3);
    backdrop-filter: blur(30px);
}

.card header {
    margin-bottom: 2rem;
}

.card header h2 {
    font-size: 1rem;
    font-weight: 600;
}

.section-info .info {
    flex-grow: 1;
    padding-right: 2rem;
}

.section-info p {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}

.section-info p .right {
    display: flex;
    flex-direction: column;
}

.profile-img {
    width: 12rem;
    height: 12rem;
}

.skills {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
}

.skill-container {
    position: relative;
    width: 150px;
    height: 150px;
}

.skill-container img {
    width: 60px;
    height: 60px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.works {
    display: flex;
    flex-direction:row;
    flex-wrap: wrap;
}

.works a {
    width: 400px;
}

.works a img {
    max-width: 100%;
    opacity: 0.8;
}
.works a:hover img {
    opacity: 1;
}
</style>