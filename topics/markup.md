# Markup portfolio

## 1. Structure a site using semantic HTML to aid accessibility

Using semantic HTML elements aids accessibility by better representing the functionality of parts of the site. This is especially helpful for screen readers. 

Our project used semantic HTML elements instead of more generic elements like so:

```html:
<header>
<nav></nav>
</header>
...
<section id="title">
</section>
```

Users can determine the purpose of our elements at a glance. Here we used `<header>`, `<nav>`, and `<section>` elements, over `<div>` in order to indicate their purpose. We used `<div>` and `<span>` elements for layout purposes within more semantic sections.

---

## 2. Make a web page more readable for screen readers

In addition to the semantic HTML elements aforementioned, we ensured our `<img>` elements included alt-text and used aria parameters for elements in the form that would otherwise be anonymous. 

```html!
<img src="./images/portfolio-1.jpeg" alt="screenshot of a website design of two large rows, spanning the full width of its page" />
```

---

## 3. Design a UI without relying solely on colour, so that we don’t exclude colour-blind users

The site design relies on sections with a dark/light contrast between each, rather than colour. The functionality does not rely on colour to differeniate elements. 

For example, the navigation bar uses hover states with a dark to light hover state to inform the user of a link. A pointer is also used to indicate this furhter. 


>![](https://i.imgur.com/t1cjITo.png)

inactive hover state link

--

![](https://i.imgur.com/0meEn0i.png)

> active hover state link (plus mouse pointer)

---

## 4. Ensure our UI has sufficient colour contrast so that everyone can perceive it comfortably

https://contrast-ratio.com/

## 5. Use various tools to check that a website meets accessibility criteria

I predominately used Chrome DevTools' [Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/#:~:text=It%20has%20audits%20for%20performance,how%20well%20the%20page%20did.) feature for cross-checking the site's accessibility criteria. 

![](https://i.imgur.com/gAaquAw.png)


The final score was 95, with room to improve colour contrast on a few elements. 

![](https://i.imgur.com/Pb0qzqr.png)

The report details passing audits, such as proving alt text for images, sequential h1-h6 elements, as well as declaring thwe site's language, to name a few. 

![](https://i.imgur.com/6Cx4LeW.png)


Towards the latter stages of the project, I used various sites for cross-checking the contrast ratio, as well as good Web Accessibility practice. 

https://webaim.org/resources/contrastchecker/
and
https://contrast-ratio.com/

Unfortunately, I did not have time to correct these before the site was submitted. 

## 6. Ensure a website displays well on screens of different sizes



## 7. Use CSS media queries to ensure content is always presented effectively

## 8. Demonstrate a mobile-first approach to designing a website with a great user experience

## 9. Create an attractive and accessible colour palette for a project

We determined a colour palette for the project using coolers. We selected colour matches for various elements to maximise the contrast. 

https://coolors.co/ffffff-313131-e4572e-7fb069-fbaf00

Unfortunately, there were a few missed lower contrast ratios. Notably, the failed audits had a contrast ratio of 2:52:1 (#fff on #7fb069), where the standard for Web Accessibility is 4:5:1.  

## 10. Use CSS variables to apply repeated colours to HTML elements
