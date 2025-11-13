<template>
  <section class="invite"> 
    <div class="card">
      <!-- Дата приглашения сверху -->
      <div class="invitation-date">
        <div class="date-badge">
          <span class="date-number">20</span>
          <span class="date-month">Ноябрь 2025</span>
        </div>
      </div>

      <div class="header">
        <div class="logo-container">
          <!-- Замените путь на правильный для вашего проекта -->
          <img src="./logo/logo.jpg" alt="LOGO-BILIM" class="logo-image" v-if="hasLogo">
          <div class="logo-text" v-else>LOGO-BILIM</div>
        </div>
        <h1>Приглашение на открытие</h1>
        <p class="subtitle">Логопедический центр для детей</p>
      </div>

      <div class="body">
        <p class="greeting">Уважаемые родители и друзья!</p>
        <p class="intro">
          Мы с радостью приглашаем вас на торжественное открытие нашего нового логопедического центра, 
          где каждый ребёнок получит профессиональную помощь и заботу.
        </p>

        <div class="services">
          <h3>Наши услуги:</h3>
          <div class="services-grid">
            <div class="service-item">
              <div class="service-icon">🗣️</div>
              <h4>Логопед-дефектолог</h4>
              <p>Коррекция речи и развитие коммуникативных навыков</p>
            </div>
            <div class="service-item">
              <div class="service-icon">🌟</div>
              <h4>Сенсорная интеграция</h4>
              <p>Развитие восприятия и обработки сенсорной информации</p>
            </div>
            <div class="service-item">
              <div class="service-icon">💆</div>
              <h4>Детский массаж</h4>
              <p>Расслабляющий и лечебный массаж для детей</p>
            </div>
            <div class="service-item">
              <div class="service-icon">🧩</div>
              <h4>АВА-терапия</h4>
              <p>Прикладной анализ поведения для развития навыков</p>
            </div>
          </div>
        </div>

        <div class="details-container">
          <ul class="details">
            <li>
              <strong>📅 Дата:</strong> 20 ноября 2025
            </li>
            <li>
              <strong>⏰ Время:</strong> 18:00
            </li>
            <li>
              <strong>📍 Место:</strong> Креативное пространство "ЛОГО-БИЛИМ"<br>
              <span class="address">ул. Кураманжан Датка 506</span>
              <a href="https://yandex.com/maps/10310/osh/house/Y0sYcQBpS0AOQFpqfXl1eHVgYw==/?ll=72.779338%2C40.549861&z=20.28" 
                 target="_blank" class="map-link">
                 🗺️ Посмотреть на карте
              </a>
            </li>
          </ul>
        </div>

        <!-- Карта -->
        <div class="map-container">
          <h3>Мы находимся здесь:</h3>
          <div class="map-placeholder">
            <a href="https://yandex.com/maps/10310/osh/house/Y0sYcQBpS0AOQFpqfXl1eHVgYw==/?ll=72.779338%2C40.549861&z=20.28" 
               target="_blank" class="map-button">
              <div class="map-icon">🗺️</div>
              <div class="map-text">
                <strong>Открыть карту</strong>
                <span>ул. Кураманжан Датка 506, Ош</span>
              </div>
            </a>
          </div>
        </div>

        <div class="highlights">
          <p class="highlights-title">🎉 В программе:</p>
          <ul class="highlights-list">
            <li>Экскурсия по центру</li>
            <li>Консультации специалистов</li>
            <li>Мастер-классы для детей</li>
            <li>Фуршет и подарки</li>
          </ul>
        </div>
      </div>

      <div class="actions">
        <button class="btn primary" @click="confirmVisit">
          {{ confirmed ? '✅ Ждём вас!' : 'Подтвердить участие' }}
        </button>
        <div class="guest-count" v-if="confirmed">
          Уже подтвердили: {{ guestCount }} гостей
        </div>
      </div>

      <footer class="footer">
        <div class="contact-info">
          <span class="phone">📞 +996 (998) 605-605</span>
          <span class="separator">|</span>
          <a href="https://www.instagram.com/logo_bilim_osh"
             target="_blank"
             rel="noopener"
             class="insta-link">
            <svg class="insta-icon" viewBox="0 0 24 24" fill="currentColor">
              <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/>
            </svg>
            logo_bilim_osh
          </a>
        </div>
      </footer>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const confirmed = ref(false)
const guestCount = ref(23)
const hasLogo = ref(false) // установите true если добавите логотип

const confirmVisit = () => {
  confirmed.value = true
  guestCount.value += 1
}
</script>

<style scoped>
.invite {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  padding: 40px 16px;
  background: linear-gradient(135deg, #f0f4ff 0%, #e8f0ff 50%, #d9e4ff 100%);
  font-family: 'Inter', system-ui, -apple-system, 'Segoe UI', Roboto, sans-serif;
}

.card {
  max-width: 800px;
  width: 100%;
  background: white;
  border-radius: 24px;
  box-shadow: 
    0 20px 40px rgba(67, 97, 238, 0.15),
    0 8px 16px rgba(67, 97, 238, 0.1);
  padding: 40px;
  border: 1px solid rgba(255, 255, 255, 0.8);
  text-align: center;
  position: relative;
}

/* Дата приглашения сверху */
.invitation-date {
  position: absolute;
  top: -20px;
  right: 30px;
  z-index: 10;
}

.date-badge {
  background: linear-gradient(135deg, #4361ee, #7209b7);
  color: white;
  padding: 12px 16px;
  border-radius: 12px;
  box-shadow: 0 8px 20px rgba(67, 97, 238, 0.3);
  text-align: center;
  min-width: 80px;
}

.date-number {
  display: block;
  font-size: 1.8em;
  font-weight: 800;
  line-height: 1;
}

.date-month {
  display: block;
  font-size: 0.9em;
  font-weight: 600;
  opacity: 0.9;
}

.header {
  margin-bottom: 32px;
  border-bottom: 2px solid #eef4ff;
  padding-bottom: 20px;
  padding-top: 10px;
}

.logo-container {
  margin-bottom: 20px;
}

.logo-image {
  max-width: 200px;
  height: auto;
  margin: 0 auto;
}

.logo-text {
  font-size: 2.5em;
  font-weight: 800;
  color: #4361ee;
  margin-bottom: 16px;
  text-shadow: 2px 2px 4px rgba(67, 97, 238, 0.1);
}

.header h1 {
  margin: 0;
  font-size: 2.2em;
  color: #3a56e4;
  font-weight: 700;
}

.subtitle {
  margin: 8px 0 0 0;
  color: #7209b7;
  font-size: 1.2em;
  font-weight: 500;
}

.body {
  color: #37474f;
  line-height: 1.7;
  text-align: center;
}

.greeting {
  font-size: 1.3em;
  font-weight: 600;
  color: #4361ee;
  margin-bottom: 16px;
}

.intro {
  font-size: 1.1em;
  margin-bottom: 32px;
  color: #455a64;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

.services {
  margin: 32px 0;
  padding: 24px;
  background: #f8fbff;
  border-radius: 16px;
  border-left: 4px solid #4361ee;
}

.services h3 {
  color: #3a56e4;
  margin-bottom: 20px;
  font-size: 1.4em;
}

/* Обновленная сетка услуг - по 2 в строке */
.services-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
  margin-top: 20px;
}

.service-item {
  text-align: center;
  padding: 20px;
  background: white;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(67, 97, 238, 0.1);
  transition: transform 0.3s ease;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 180px;
}

.service-item:hover {
  transform: translateY(-5px);
}

.service-icon {
  font-size: 2.5em;
  margin-bottom: 12px;
}

.service-item h4 {
  color: #3a56e4;
  margin: 8px 0;
  font-size: 1.1em;
}

.service-item p {
  color: #546e7a;
  font-size: 0.9em;
  line-height: 1.4;
  margin: 0;
}

.details-container {
  display: flex;
  justify-content: center;
  margin: 32px 0;
}

.details {
  list-style: none;
  padding: 0;
  background: #eef4ff;
  padding: 24px;
  border-radius: 16px;
  text-align: left;
  max-width: 400px;
  width: 100%;
}

.details li {
  padding: 12px 0;
  border-bottom: 1px dashed #a5b4fc;
  font-size: 1.1em;
}

.details li:last-child {
  border-bottom: none;
}

.address {
  margin-left: 0;
  color: #546e7a;
  font-size: 0.95em;
  display: block;
  margin-top: 5px;
}

.map-link {
  display: inline-block;
  margin-top: 8px;
  color: #4361ee;
  text-decoration: none;
  font-weight: 500;
  font-size: 0.9em;
  transition: color 0.3s ease;
}

.map-link:hover {
  color: #7209b7;
  text-decoration: underline;
}

/* Стили для карты */
.map-container {
  margin: 32px 0;
  padding: 24px;
  background: #f8fbff;
  border-radius: 16px;
  border-left: 4px solid #7209b7;
}

.map-container h3 {
  color: #3a56e4;
  margin-bottom: 16px;
  font-size: 1.3em;
}

.map-placeholder {
  background: linear-gradient(135deg, #edf2ff, #f3e8ff);
  border-radius: 12px;
  padding: 20px;
  border: 2px dashed #a5b4fc;
}

.map-button {
  display: flex;
  align-items: center;
  justify-content: center;
  text-decoration: none;
  color: inherit;
  gap: 15px;
  transition: transform 0.3s ease;
}

.map-button:hover {
  transform: scale(1.05);
}

.map-icon {
  font-size: 3em;
}

.map-text {
  text-align: left;
}

.map-text strong {
  display: block;
  color: #4361ee;
  font-size: 1.1em;
  margin-bottom: 4px;
}

.map-text span {
  color: #546e7a;
  font-size: 0.9em;
}

.highlights {
  background: linear-gradient(135deg, #edf2ff, #f3e8ff);
  padding: 20px;
  border-radius: 16px;
  margin: 24px auto;
  max-width: 500px;
}

.highlights-title {
  font-weight: 600;
  color: #7209b7;
  margin-bottom: 12px;
}

.highlights-list {
  list-style: none;
  padding: 0;
  text-align: left;
  max-width: 300px;
  margin: 0 auto;
}

.highlights li {
  padding: 6px 0;
  color: #455a64;
}

.highlights li:before {
  content: "✨ ";
}

.actions {
  margin: 32px 0;
  padding-top: 24px;
  border-top: 2px solid #eef4ff;
}

.btn {
  padding: 16px 32px;
  border-radius: 50px;
  border: none;
  font-size: 1.1em;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  margin: 8px;
}

.btn.primary {
  background: linear-gradient(135deg, #4361ee, #7209b7);
  color: white;
  box-shadow: 0 4px 15px rgba(67, 97, 238, 0.3);
}

.btn.primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(67, 97, 238, 0.4);
}

.guest-count {
  margin-top: 16px;
  color: #78909c;
  font-style: italic;
}

/* Компактный футер */
.footer {
  margin-top: 24px;
  padding-top: 16px;
  border-top: 1px solid #e0e0e0;
  text-align: center;
}

.contact-info {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 12px;
  font-size: 0.9em;
  color: #546e7a;
}

.phone {
  font-weight: 500;
}

.separator {
  color: #b0b0b0;
}

.insta-link {
  display: flex;
  align-items: center;
  gap: 6px;
  color: #e4405f;
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s ease;
}

.insta-link:hover {
  color: #b5179e;
  text-decoration: underline;
}

.insta-icon {
  width: 16px;
  height: 16px;
  flex-shrink: 0;
}

@media (max-width: 768px) {
  .card {
    padding: 24px;
    margin: 16px;
  }
  
  .invitation-date {
    position: static;
    margin-bottom: 20px;
    display: flex;
    justify-content: center;
  }
  
  .date-badge {
    padding: 10px 14px;
  }
  
  .header h1 {
    font-size: 1.8em;
  }
  
  .logo-text {
    font-size: 2em;
  }
  
  /* На планшетах тоже оставляем 2 в строке */
  .services-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 15px;
  }
  
  .service-item {
    padding: 15px;
    min-height: 160px;
  }
  
  .btn {
    padding: 14px 28px;
    font-size: 1em;
  }
  
  .details {
    text-align: center;
  }
  
  .map-button {
    flex-direction: column;
    text-align: center;
  }
  
  .map-text {
    text-align: center;
  }
  
  .contact-info {
    font-size: 0.85em;
    gap: 8px;
  }
}

@media (max-width: 480px) {
  .card {
    padding: 20px;
  }
  
  .header h1 {
    font-size: 1.6em;
  }
  
  .details li {
    font-size: 1em;
  }
  
  /* На мобильных переходим на 1 колонку */
  .services-grid {
    grid-template-columns: 1fr;
    gap: 15px;
  }
  
  .service-item {
    min-height: 140px;
    padding: 15px 10px;
  }
  
  .service-icon {
    font-size: 2em;
  }
  
  .service-item h4 {
    font-size: 1em;
  }
  
  .service-item p {
    font-size: 0.85em;
  }
  
  .contact-info {
    flex-direction: column;
    gap: 6px;
  }
  
  .separator {
    display: none;
  }
}
</style>