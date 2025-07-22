# Cyber Capstone - Complete API Documentation

## Table of Contents
1. [Overview](#overview)
2. [JavaScript APIs](#javascript-apis)
3. [Alpine.js Components](#alpinejs-components)
4. [UI Components](#ui-components)
5. [Interactive Features](#interactive-features)
6. [Third-Party Libraries](#third-party-libraries)
7. [CSS Classes](#css-classes)
8. [Usage Examples](#usage-examples)

## Overview

This documentation covers all public APIs, functions, and components in the Cyber Capstone project - a modern web application built with Tailwind CSS, Alpine.js, and various interactive libraries.

## JavaScript APIs

### Core Application Functions

#### Navigation Controller
```javascript
// Sticky menu functionality
@scroll.window="stickyMenu = (window.pageYOffset > 20) ? true : false"
```
**Purpose**: Controls the sticky navigation behavior
**Parameters**: None
**Usage**: Automatically triggered on scroll

#### Theme Controller
```javascript
// Dark mode toggle
darkMode = JSON.parse(localStorage.getItem('darkMode'));
$watch('darkMode', value => localStorage.setItem('darkMode', JSON.stringify(value)))
```
**Purpose**: Manages dark/light theme switching with persistence
**Parameters**: 
- `darkMode`: Boolean value
**Returns**: Stored theme preference

#### Mobile Navigation
```javascript
@click="navigationOpen = !navigationOpen"
```
**Purpose**: Toggles mobile navigation menu
**Parameters**: None
**Usage**: Attached to hamburger menu button

### Pricing Table API

#### Setup Function
```javascript
const setup = () => {
  return {
    isNavOpen: false,
    billPlan: "monthly",
    plans: [
      {
        name: "Starter",
        price: {
          monthly: 29,
          annually: 29 * 12 - 199,
        },
        features: [
          "400 GB Storage",
          "Unlimited Photos & Videos",
          "Exclusive Support",
        ],
      },
      // ... more plans
    ],
  };
};
```
**Purpose**: Initializes pricing table with plan data
**Returns**: Object containing pricing configuration
**Usage**: 
```javascript
const pricingData = setup();
```

### Scroll Functionality

#### Back to Top
```javascript
@click="window.scrollTo({top: 0, behavior: 'smooth'})"
@scroll.window="scrollTop = (window.pageYOffset > 50) ? true : false"
```
**Purpose**: Smooth scroll to top with visibility control
**Parameters**: None
**Usage**: Automatically shows/hides based on scroll position

## Alpine.js Components

### Page State Management
```javascript
x-data="{ 
  page: 'home', 
  'darkMode': true, 
  'stickyMenu': false, 
  'navigationOpen': false, 
  'scrollTop': false 
}"
```
**Properties**:
- `page`: Current page identifier
- `darkMode`: Theme state
- `stickyMenu`: Navigation sticky state
- `navigationOpen`: Mobile menu state
- `scrollTop`: Scroll position state

### Section Title Component
```javascript
x-data="{ 
  sectionTitle: 'Client\'s Testimonials', 
  sectionTitleText: 'Long description text...'
}"
```
**Purpose**: Dynamic section titles and descriptions
**Properties**:
- `sectionTitle`: Main heading text
- `sectionTitleText`: Subtitle/description

### Project Filter Component
```javascript
x-data="{filterTab: 1}"
```
**Purpose**: Controls project category filtering
**Methods**:
- `@click="filterTab = 1"`: Set active filter
- `:class="{ 'gh lk' : filterTab === 1 }"`: Apply active styles

## UI Components

### Header Component
**Location**: Lines 23-201 in index.html
**Features**:
- Responsive navigation
- Dark/light mode toggle
- Mobile hamburger menu
- Sticky scroll behavior

**API**:
```html
<header class="g s r vd ya cj" :class="{ 'hh sm _k dj bl ll' : stickyMenu }">
  <!-- Logo, navigation, theme toggle -->
</header>
```

### Hero Section
**Location**: Lines 204-256 in index.html
**Features**:
- Call-to-action buttons
- Background shapes
- Responsive layout

### Features Section
**Location**: Lines 258-299 in index.html
**API**:
```html
<section id="features">
  <!-- Feature items with icons and descriptions -->
</section>
```

### Team Section
**Location**: Lines 350-650 in index.html
**Features**:
- Team member cards
- Social media links
- Responsive grid layout

### Projects Section
**Location**: Lines 750-950 in index.html
**Features**:
- Isotope filtering
- Project categories
- Hover effects

### Testimonials Section
**Location**: Lines 1000-1200 in index.html
**Features**:
- Swiper carousel
- Customer testimonials
- Brand logos

### Contact Section
**Location**: Lines 1340-1600 in index.html
**Features**:
- Contact form
- Form validation
- Submit handling

**Form API**:
```html
<form>
  <input id="fullname" type="text" placeholder="Full Name" />
  <input id="email" type="email" placeholder="Email Address" />
  <input id="phone" type="text" placeholder="Phone Number" />
  <input id="subject" type="text" placeholder="Subject" />
  <textarea id="message" placeholder="Message"></textarea>
</form>
```

## Interactive Features

### Isotope Grid Filtering
```javascript
// Initialize Isotope
var iso = new Isotope('.projects-wrapper', {
  itemSelector: '.project-item',
  layoutMode: 'masonry'
});

// Filter functionality
projectTabBTN.forEach(function (btn) {
  btn.addEventListener('click', function () {
    var selector = btn.getAttribute('data-filter');
    iso.arrange({
      filter: selector
    });
  });
});
```

**Usage**:
```html
<button data-filter="*">All</button>
<button data-filter=".branding">Branding</button>
<button data-filter=".digital">Digital</button>
```

### Swiper Carousel
```javascript
// Testimonial slider
<div class="swiper testimonial-01">
  <div class="swiper-wrapper">
    <div class="swiper-slide">
      <!-- Testimonial content -->
    </div>
  </div>
</div>
```

**Navigation**:
```html
<div class="swiper-button-prev"></div>
<div class="swiper-button-next"></div>
```

## Third-Party Libraries

### Alpine.js
**Version**: 3.10.3
**Purpose**: Reactive UI components
**Documentation**: [Alpine.js Documentation](https://alpinejs.dev/)

### Isotope Layout
**Purpose**: Grid filtering and masonry layout
**Usage**: Project portfolio filtering

### Swiper
**Purpose**: Touch-enabled carousels
**Usage**: Testimonials slider

### AOS (Animate On Scroll)
**Purpose**: Scroll animations
**Initialization**:
```javascript
AOS.init();
```

### ScrollReveal
**Purpose**: Advanced scroll animations
**Usage**: Element reveal effects

### FSLightbox
**Purpose**: Image and video lightbox
**Usage**: Portfolio media viewing

## CSS Classes

### Utility Classes
- `tc`: Text center
- `wf`: Width full
- `xf`: Flex
- `gg`: Grid gap
- `tc sf`: Text center small font
- `ek`: Text color
- `pg`: Padding
- `mb`: Margin bottom

### Component Classes
- `.project-item`: Individual project cards
- `.project-tab-btn`: Filter buttons
- `.swiper-slide`: Carousel slides
- `.animate_top`, `.animate_left`, `.animate_right`: Animation classes

### State Classes
- `.gh lk`: Active state
- `.om`: Light mode
- `.nm`: Dark mode
- `.uc`: Scroll top visible

## Usage Examples

### Creating a New Project Filter
```html
<button 
  data-filter=".new-category"
  @click="filterTab = 5"
  :class="{ 'gh lk' : filterTab === 5 }"
  class="project-tab-btn ek rg ml il vi mi"
>
  New Category
</button>

<div class="project-item wi fb vd jn/2 to/3 new-category">
  <!-- Project content -->
</div>
```

### Adding a New Testimonial
```html
<div class="swiper-slide">
  <div class="i hh rm sg vk xm bi qj">
    <div class="tc sf rn tn un zf dp">
      <img class="bf" src="images/new-testimonial.png" alt="User" />
      <div>
        <img src="images/icon-quote.svg" alt="Quote" />
        <p class="ek ik xj _p kc fb">
          New testimonial text here...
        </p>
        <div class="tc yf vf">
          <div>
            <span class="rc ek xj kk wm zb">Customer Name</span>
            <span class="rc">Position @company</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
```

### Implementing Dark Mode Toggle
```html
<input 
  type="checkbox" 
  :checked="darkMode" 
  @change="darkMode = !darkMode"
  class="pf vd yc uk h r za ab"
/>
```

### Adding Scroll Animation
```html
<div 
  data-aos="fade-up" 
  class="animate_top"
>
  <!-- Content to animate -->
</div>
```

### Custom Section with Alpine.js
```html
<section 
  x-data="{ 
    sectionTitle: 'Custom Section', 
    sectionTitleText: 'Custom description',
    items: []
  }"
>
  <h2 x-text="sectionTitle" class="fk vj pr kk wm"></h2>
  <p x-text="sectionTitleText" class="bb on/5 wo/5 hq"></p>
  
  <template x-for="item in items" :key="item.id">
    <div x-text="item.name"></div>
  </template>
</section>
```

## Browser Support
- Modern browsers supporting ES6+
- Alpine.js requires IE11+ or modern browsers
- Touch events supported on mobile devices
- Responsive design for all screen sizes

## Performance Considerations
- Images are optimized and served in modern formats
- JavaScript is bundled and minified
- CSS classes are utility-first for optimal file size
- Animations use CSS transforms for better performance

## Accessibility Features
- Semantic HTML structure
- ARIA labels and roles
- Keyboard navigation support
- Focus management
- Screen reader compatibility

This documentation provides comprehensive coverage of all public APIs, components, and functionality available in the Cyber Capstone project. Each section includes practical examples and usage instructions for easy implementation.