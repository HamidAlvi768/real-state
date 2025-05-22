Here's the relevant code:

**HTML (index.html):**

The core HTML structure for the navbar and the overlay menu is within the `<header>` section.

```html
<!DOCTYPE html>
<html>
  <head>
    <link rel="stylesheet" type="text/css" href="css/bootstrap.css" />
    <link href="css/style.css" rel="stylesheet" />
    <link href="css/responsive.css" rel="stylesheet" />
  </head>
  <body>
    <div class="hero_area">
      <header class="header_section">
        <div class="container-fluid">
          <nav class="navbar navbar-expand-lg custom_nav-container">
            <a class="navbar-brand" href="index.html">
              <img class="home-logo" src="images/logo.png" alt="" />
            </a>
            <div class="navbar-collapse" id="">
              <ul class="navbar-nav justify-content-between "></ul>

              <div class="custom_menu-btn">
                <button onclick="openNav()">
                  <span class="s-1"></span>
                  <span class="s-2"></span>
                  <span class="s-3"></span>
                </button>
              </div>
              <div id="myNav" class="overlay">
                <div class="overlay-content">
                  <a href="index.html">HOME</a>
                  <a href="about.html">ABOUT</a>
                  <a href="house.html">HOUSE</a>
                  <a href="contact.html">CONTACT US</a>
                </div>
              </div>
            </div>
          </nav>
        </div>
      </header>
    </div>

    <script type="text/javascript" src="js/jquery-3.4.1.min.js"></script>
    <script type="text/javascript" src="js/bootstrap.js"></script>
    <script type="text/javascript" src="js/custom.js"></script>
  </body>
</html>
```

**CSS (css/style.css - relevant parts):**

These are the styles that directly affect the appearance and behavior of the custom collapsible navbar/sidebar.

```css
/*Red*/
:root {
  --primary1: #b97630;
  --primary2: #8c3232;
}
/*Blue*/
/* :root{
  --primary1: #3554d1 ;
  --primary2: #0f2480;
} */

/*header section*/
.hero_area {
  /* ... (other styles, background-image might be relevant for context) ... */
  position: relative; /* Often used for positioning child elements */
}

.sub_page .hero_area {
  /* ... */
}

.header_section {
  overflow-x: hidden; /* Can be important for sidebars that slide in/out */
}

.header_section .container-fluid {
  padding-right: 25px;
  padding-left: 25px;
}

.custom_nav-container.navbar-expand-lg .navbar-nav {
  /* ... (styles for standard nav links, not directly for the overlay menu button) ... */
}

a,
a:hover,
a:focus {
  text-decoration: none;
}

.navbar-brand img {
  width: 50px;
}
.navbar-brand .home-logo {
  width: 100px !important;
}

.custom_nav-container {
  position: relative;
  z-index: 99999; /* Ensures navbar is on top */
  padding: 0;
  height: 80px; /* Fixed height for the navbar */
}

.custom_nav-container .navbar-toggler {
  /* Standard Bootstrap toggler, not used here for the overlay */
  outline: none;
}

.custom_nav-container .navbar-toggler .navbar-toggler-icon {
  /* ... */
}

*
  Add
  background
  to
  mobile
  menu
  and
  adjust
  positioning
  */
  @media screen and (max-width: 991px) {
  .navbar-collapse {
    background: #ffffff;
    width: 100%;
    height: 100vh;
    position: fixed;
    top: 0px;
    left: 0px;
    padding: 10px;
    z-index: 999;
  }

  /* Style the mobile menu links */
  .custom_nav-container .navbar-nav {
    flex-direction: column;
  }

  .custom_nav-container .nav-item {
    margin: 5px 0;
  }

  /* Ensure WhatsApp link is visible in mobile menu */
  .navbar-whatsapp {
    justify-content: center;
    padding: 10px;
  }
}

/* Styles for the custom hamburger button */
.custom_menu-btn {
  z-index: 9; /* Ensures button is clickable over other elements */
  position: absolute; /* Positioned relative to the navbar */
  right: 15px;
  top: 7px;
}

.custom_menu-btn button {
  margin-top: 12px;
  outline: none;
  border: none;
  background-color: transparent;
}

.custom_menu-btn button span {
  display: block;
  width: 50px;
  height: 5px;
  background-color: #fff; /* Hamburger icon color */
  margin: 6px 0;
  -webkit-transition: all 0.3s;
  transition: all 0.3s;
}

/* Specific styles for the hamburger spans (if any for animation, though not apparent here beyond structure) */
.custom_menu-btn .s-2 {
  width: 25px; /* Shorter middle bar */
  margin-left: auto;
}

.custom_menu-btn .s-3 {
  width: 25px; /* Shorter bottom bar */
  margin-left: auto;
}

/* Styles for the overlay menu */
.overlay {
  height: 100%;
  width: 0; /* Initially hidden, will be changed by JavaScript */
  position: fixed; /* Stays in place during scroll */
  z-index: 100000; /* Higher than navbar to cover it when open, though navbar itself is 99999 */
  /* Note: z-index: 1 was in the original, but likely needs to be higher */
  top: 0;
  left: 0;
  background-color: black; /* Fallback */
  background-color: rgba(
    53,
    84,
    209,
    0.9
  ); /* Semi-transparent background, original had a blue color */
  /* Consider changing this to var(--primary2) or similar for consistency if needed */
  overflow-x: hidden; /* Prevent horizontal scroll */
  -webkit-transition: 0.5s; /* Smooth transition for opening/closing */
  transition: 0.5s;
}

.overlay .closebtn {
  /* A close button, not present in the HTML but common for overlays */
  position: absolute;
  top: 0;
  right: 30px;
  font-size: 60px;
}

.overlay a {
  padding: 0px; /* Original was 0px, might need adjustment for better spacing */
  text-decoration: none;
  font-size: 22px;
  color: #f1f1f1; /* Link color in the overlay */
  display: block; /* Each link on a new line */
  -webkit-transition: 0.3s; /* Smooth transition for hover effect */
  transition: 0.3s;
  margin-bottom: 15px;
}

.overlay a:hover {
  color: #252525; /* Link hover color */
}

.overlay-content {
  position: relative;
  top: 30%; /* Position content vertically */
  width: 100%;
  text-align: center;
  margin-top: 30px;
}

/* This class is likely added by JavaScript to open the menu */
.menu_width {
  width: 100%;
}

/* Potentially relevant from responsive.css if there are specific overrides for navbar/overlay on different screen sizes */
/* (You would need to check css/responsive.css for styles targeting these classes) */
```

**JavaScript (Conceptual - from `js/custom.js`):**

The provided HTML uses an `onclick="openNav()"` attribute. The JavaScript function `openNav()` (and likely a corresponding `closeNav()` function, though not explicitly shown in the HTML for a close button) would be in `js/custom.js`. It would typically do something like this:

```javascript
// This is a conceptual representation of what might be in js/custom.js
// The actual implementation might vary.

function openNav() {
  document.getElementById("myNav").style.width = "100%";
  // Or add a class: document.getElementById("myNav").classList.add("menu_width");
}

// A close function would typically be called by a close button inside the overlay
function closeNav() {
  document.getElementById("myNav").style.width = "0%";
  // Or remove a class: document.getElementById("myNav").classList.remove("menu_width");
}

// Example for a close button if it existed (e.g., <a href="javascript:void(0)" class="closebtn" onclick="closeNav()">&times;</a>)
// The provided HTML doesn't have an explicit close button in the overlay,
// so closing might be handled by clicking a link or outside the menu.
```
