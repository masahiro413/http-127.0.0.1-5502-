/* LUMIÈRE — LP Script */

// --- Hamburger / Drawer ---
const hamburger = document.getElementById('js-hamburger');
const drawer    = document.getElementById('js-drawer');
hamburger.addEventListener('click', () => {
  const open = hamburger.classList.toggle('is-open');
  drawer.classList.toggle('is-open', open);
});
// close drawer on link click
drawer.querySelectorAll('a').forEach(a => {
  a.addEventListener('click', () => {
    hamburger.classList.remove('is-open');
    drawer.classList.remove('is-open');
  });
});

// --- Header scroll shadow ---
const header = document.querySelector('.header');
window.addEventListener('scroll', () => {
  header.classList.toggle('is-scrolled', window.scrollY > 40);
  // page top
  document.getElementById('js-pagetop')
    .classList.toggle('is-show', window.scrollY > 200);
}, { passive: true });

// --- Floating petals ---
const petalContainer = document.getElementById('js-petals');
const PETAL_COUNT = 18;
const COLORS = ['#C4627A', '#e8889a', '#C9A96E', '#d4aaa0', '#8BAF8E'];

for (let i = 0; i < PETAL_COUNT; i++) {
  const p = document.createElement('div');
  p.className = 'petal';
  const size   = 6 + Math.random() * 10;
  const left   = Math.random() * 100;
  const delay  = Math.random() * 14;
  const dur    = 10 + Math.random() * 12;
  const color  = COLORS[Math.floor(Math.random() * COLORS.length)];
  const rotate = Math.random() * 60 - 30;
  Object.assign(p.style, {
    left:            `${left}%`,
    width:           `${size}px`,
    height:          `${size * 1.5}px`,
    background:      color,
    opacity:         0.25 + Math.random() * 0.25,
    animationDelay:  `${delay}s`,
    animationDuration:`${dur}s`,
    transform:       `rotate(${rotate}deg)`,
    borderRadius:    Math.random() > 0.5 ? '50% 0 50% 0' : '0 50% 0 50%',
  });
  petalContainer.appendChild(p);
}

// --- Scroll reveal ---
const revealEls = document.querySelectorAll('.reveal');
const io = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.classList.add('is-visible');
      io.unobserve(e.target);
    }
  });
}, { threshold: 0.12 });
revealEls.forEach(el => io.observe(el));

// --- Smooth scroll for anchor links ---
document.querySelectorAll('a[href^="#"]').forEach(a => {
  a.addEventListener('click', e => {
    const id = a.getAttribute('href');
    if (id === '#') return;
    const target = document.querySelector(id);
    if (!target) return;
    e.preventDefault();
    const top = target.getBoundingClientRect().top + window.scrollY - 68;
    window.scrollTo({ top, behavior: 'smooth' });
  });
});
