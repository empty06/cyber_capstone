# Cyber Capstone - Quick Reference Guide

## Essential APIs & Components

### Alpine.js Quick Reference

#### Basic Component Structure
```javascript
x-data="{ 
  // State properties
  isOpen: false,
  count: 0,
  items: []
}"
```

#### Common Directives
| Directive | Purpose | Example |
|-----------|---------|---------|
| `x-data` | Initialize component state | `x-data="{ open: false }"` |
| `x-show` | Toggle visibility | `x-show="open"` |
| `x-if` | Conditional rendering | `x-if="items.length > 0"` |
| `x-for` | Loop through arrays | `x-for="item in items"` |
| `x-text` | Set text content | `x-text="message"` |
| `x-model` | Two-way data binding | `x-model="email"` |
| `@click` | Click event handler | `@click="toggle()"` |
| `:class` | Dynamic classes | `:class="{ 'active': isActive }"` |

### Navigation Control

#### Sticky Header
```javascript
@scroll.window="stickyMenu = (window.pageYOffset > 20) ? true : false"
:class="{ 'hh sm _k dj bl ll' : stickyMenu }"
```

#### Mobile Menu Toggle
```javascript
@click="navigationOpen = !navigationOpen"
:class="{ 'd hh rm sr td ud qg ug jc yh': navigationOpen }"
```

#### Dark Mode Toggle
```javascript
@change="darkMode = !darkMode"
:class="{'b eh': darkMode === true}"
```

### Project Filtering (Isotope)

#### Initialize Filter
```javascript
var iso = new Isotope('.projects-wrapper', {
  itemSelector: '.project-item',
  layoutMode: 'masonry'
});
```

#### Filter Items
```javascript
projectTabBTN.forEach(function (btn) {
  btn.addEventListener('click', function () {
    var selector = btn.getAttribute('data-filter');
    iso.arrange({ filter: selector });
  });
});
```

#### Filter Button Structure
```html
<button data-filter="*" class="project-tab-btn">All</button>
<button data-filter=".branding" class="project-tab-btn">Branding</button>
<div class="project-item branding"><!-- Content --></div>
```

### Swiper Carousel

#### Basic Swiper Setup
```javascript
new Swiper('.swiper-container', {
  slidesPerView: 1,
  spaceBetween: 30,
  loop: true,
  autoplay: { delay: 5000 },
  navigation: {
    nextEl: '.swiper-button-next',
    prevEl: '.swiper-button-prev',
  }
});
```

#### HTML Structure
```html
<div class="swiper-container">
  <div class="swiper-wrapper">
    <div class="swiper-slide"><!-- Content --></div>
  </div>
  <div class="swiper-button-next"></div>
  <div class="swiper-button-prev"></div>
</div>
```

### Form Handling

#### Basic Form Component
```javascript
x-data="{
  form: { name: '', email: '', message: '' },
  errors: {},
  isSubmitting: false,
  
  async submitForm() {
    this.isSubmitting = true;
    // Submit logic here
    this.isSubmitting = false;
  }
}"
```

#### Form Validation
```javascript
validateEmail(email) {
  const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return regex.test(email);
}
```

### Animation Classes

#### AOS (Animate On Scroll)
```html
<div data-aos="fade-up">Content</div>
<div data-aos="fade-left">Content</div>
<div data-aos="fade-right">Content</div>
```

#### Custom Animation Classes
```html
<div class="animate_top">Animate from top</div>
<div class="animate_left">Animate from left</div>
<div class="animate_right">Animate from right</div>
```

### Utility Classes (Tailwind-based)

#### Layout
| Class | Purpose |
|-------|---------|
| `tc` | Text center |
| `wf` | Width full |
| `xf` | Flex |
| `gg` | Grid gap |
| `pg` | Padding |
| `mb` | Margin bottom |

#### States
| Class | Purpose |
|-------|---------|
| `gh lk` | Active state |
| `om` | Light mode |
| `nm` | Dark mode |
| `uc` | Scroll top visible |

### JavaScript Event Handlers

#### Scroll to Top
```javascript
@click="window.scrollTo({top: 0, behavior: 'smooth'})"
@scroll.window="scrollTop = (window.pageYOffset > 50) ? true : false"
```

#### Form Submit
```javascript
@submit.prevent="submitForm()"
```

#### Dynamic Classes
```javascript
:class="{ 'active-class': condition, 'another-class': anotherCondition }"
```

### Common Patterns

#### Loading State
```html
<template x-if="loading">
  <div class="loading-spinner">Loading...</div>
</template>
```

#### Error Handling
```html
<template x-if="error">
  <div class="error-message" x-text="error"></div>
</template>
```

#### Empty State
```html
<template x-if="!loading && items.length === 0">
  <div class="empty-state">No items found</div>
</template>
```

#### Dynamic Lists
```html
<template x-for="item in items" :key="item.id">
  <div x-text="item.name"></div>
</template>
```

### Performance Tips

#### Lazy Loading Images
```html
<img data-lazy="image" data-src="image.jpg" alt="Description">
```

#### Debounced Search
```javascript
searchInput.addEventListener('input', debounce((e) => {
  // Search logic
}, 300));
```

#### Intersection Observer
```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      // Load content
    }
  });
});
```

### Third-Party Library Initialization

#### AOS
```javascript
AOS.init();
```

#### Alpine.js
```javascript
Alpine.start();
```

#### Custom Initialization
```javascript
document.addEventListener('DOMContentLoaded', function() {
  // Initialize components
});
```

### Debugging Tips

#### Alpine.js Debugging
```javascript
// Access component data
Alpine.$data(element)

// Watch for changes
$watch('property', value => console.log(value))
```

#### Console Debugging
```javascript
console.log('Component state:', this.$data);
console.log('Element:', this.$el);
```

### Common Component IDs

| ID | Purpose |
|----|---------|
| `#features` | Features section |
| `#support` | Contact/Support section |
| `#fullname` | Contact form name field |
| `#email` | Contact form email field |
| `#message` | Contact form message field |

### CSS Selectors

| Selector | Purpose |
|----------|---------|
| `.project-item` | Project portfolio items |
| `.project-tab-btn` | Filter buttons |
| `.swiper-slide` | Carousel slides |
| `.testimonial-01` | Testimonial carousel |
| `.projects-wrapper` | Project container |

This quick reference provides the essential APIs and patterns needed for daily development with the Cyber Capstone project.