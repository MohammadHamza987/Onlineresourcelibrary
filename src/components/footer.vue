<template>
  <footer class="footer-container">
    <div class="footer-content">
      <div class="footer-info">
        <p class="creator-text">Created with ❤️ by</p>
        <h3 class="creator-name">Mohammad Hamza</h3>
        <p class="footer-description">Full Stack Developer & UI/UX Designer</p>
      </div>
      <div class="footer-actions">
        <a href="https://mohammadhamza-portfolio.netlify.app/" class="portfolio-link" target="_blank" rel="noopener noreferrer">
          <span>View Portfolio</span>
          <svg class="external-icon" fill="currentColor" viewBox="0 0 20 20">
            <path fill-rule="evenodd" d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z" clip-rule="evenodd"></path>
          </svg>
        </a>
        <div class="social-links">
          <span class="connect-text">Connect with me</span>
        </div>
      </div>
    </div>
    <div class="footer-bottom">
      <p>&copy; 2025 Learning Resources. All rights reserved.</p>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'TheFooter'
}
</script>

<style scoped>
.footer-container {
  background: linear-gradient(135deg, rgba(13, 17, 23, 0.9) 0%, rgba(219, 39, 119, 0.1) 100%);
  backdrop-filter: blur(20px);
  border-top: 1px solid rgba(236, 72, 153, 0.3);
  border-radius: 0 0 30px 30px;
  padding: 20px 24px 12px 24px;
  margin-top: 20px;
  position: relative;
  overflow: hidden;
}

.footer-container::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(236, 72, 153, 0.05) 0%, rgba(147, 51, 234, 0.02) 100%);
  pointer-events: none;
  border-radius: 0 0 30px 30px;
}

.footer-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: relative;
  z-index: 1;
  gap: 20px;
}

.footer-info {
  flex: 1;
}

.creator-text {
  margin: 0 0 4px 0;
  color: rgba(255, 255, 255, 0.7);
  font-size: 0.8rem;
  font-weight: 500;
}

.creator-name {
  margin: 0 0 4px 0;
  font-size: 1.4rem;
  font-weight: 700;
  background: linear-gradient(135deg, #ec4899 0%, #a855f7 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
}

.footer-description {
  margin: 0;
  color: rgba(255, 255, 255, 0.8);
  font-size: 0.9rem;
  font-weight: 500;
}

.footer-actions {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  gap: 8px;
}

.portfolio-link {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 8px 16px;
  background: linear-gradient(135deg, #db2777 0%, #9333ea 100%);
  color: #ffffff;
  text-decoration: none;
  border-radius: 8px;
  font-weight: 600;
  font-size: 0.9rem;
  transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
  box-shadow: 
    0 4px 15px rgba(219, 39, 119, 0.3),
    0 2px 8px rgba(0, 0, 0, 0.2),
    inset 0 1px 0 rgba(255, 255, 255, 0.2);
  position: relative;
  overflow: hidden;
}

.portfolio-link::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
  transition: left 0.5s;
}

.portfolio-link:hover::before {
  left: 100%;
}

.portfolio-link:hover {
  transform: translateY(-2px);
  box-shadow: 
    0 12px 35px rgba(219, 39, 119, 0.5),
    0 6px 15px rgba(0, 0, 0, 0.25),
    inset 0 1px 0 rgba(255, 255, 255, 0.3);
}

.external-icon {
  width: 14px;
  height: 14px;
  transition: transform 0.3s ease;
}

.portfolio-link:hover .external-icon {
  transform: translateX(2px);
}

.social-links {
  text-align: right;
}

.connect-text {
  color: rgba(236, 72, 153, 0.8);
  font-size: 0.8rem;
  font-weight: 500;
}

.footer-bottom {
  margin-top: 16px;
  padding-top: 12px;
  border-top: 1px solid rgba(236, 72, 153, 0.2);
  text-align: center;
  position: relative;
  z-index: 1;
}

.footer-bottom p {
  margin: 0;
  color: rgba(255, 255, 255, 0.6);
  font-size: 0.75rem;
}

@media (max-width: 768px) {
  .footer-container {
    padding: 16px 20px 8px 20px;
    border-radius: 0 0 25px 25px;
  }
  
  .footer-content {
    flex-direction: column;
    text-align: center;
    gap: 12px;
  }
  
  .footer-info {
    text-align: center;
  }
  
  .footer-actions {
    align-items: center;
  }
  
  .creator-name {
    font-size: 1.5rem;
  }
  
  .social-links {
    text-align: center;
  }
}

@media (max-width: 480px) {
  .portfolio-link {
    padding: 10px 20px;
    font-size: 0.9rem;
  }
  
  .creator-name {
    font-size: 1.3rem;
  }
}
</style>
