---
layout: page
title: Style Guide
permalink: /styleguide/
image: '/images/50.jpg'
---

{% include toc.html %}

* g
{:toc}

A paragraph looks like this — dolor amet cray stumptown fingerstache neutra food truck seitan poke cardigan waistcoat VHS snackwave celiac hella. Godard seitan shoreditch flexitarian next level trust fund man braid vegan listicle keytar bitters. Disrupt cray fashion axe unicorn lomo shaman poke glossier keffiyeh snackwave austin tattooed seitan hexagon lo-fi. Lumbersexual irony vaporware, butcher shaman.

***


## Cheatsheet

[HTB Academy](/cheatsheet/htbacademy.md)

## Red Team
[Pentesting Methodology](-)

[Vulnerability Assessment](-)



## Blue Team



## Tools
### Red Team Tools
### Blue Team Tools


## Write Up
* Vulnhub
* HTB / HTB Academy
* Try Hack Me
* Blabla

# Penetration Testing Methodology

## PTES
The Penetration Testing Execution Standard ([PTES](http://www.pentest-standard.org/index.php/PTES_Technical_Guidelines))  can be applied to all types of penetration tests. It outlines the  phases of a penetration test and how they should be conducted. These are  the sections in the PTES:
1. Pre-engagement Interactions
2. Intelligence Gathering
3. Threat Modeling
4. Vulnerability Analysis
5. Exploitation
6. Post Exploitation
7. Reporting

## OSSTMM
[OSSTMM](https://www.isecom.org/OSSTMM.3.pdf) is the Open Source Security Testing Methodology Manual, another set of guidelines pentesters can use to ensure they're doing  their jobs properly. It can be used alongside other pentest standards.
OSSTMM is divided into five different channels for five different areas of pentesting:
1. Human Security (human beings are subject to social engineering exploits)
2. Physical Security
3. Wireless Communications (including but not limited to technologies like WiFi and Bluetooth)
4. Telecommunications
5. Data Networks

## NIST
The [NIST](https://www.nist.gov/cyberframework) (National Institute of Standards and Technology) is well known for their NIST Cybersecurity Framework,  a system for designing incident response policies and procedures. NIST  also has a Penetration Testing Framework. The phases of the NIST  framework include:
1. Planning
1. Discovery
1. Attack
1. Reporting

## OWASP 
[OWASP](https://owasp.org) stands for the Open Web Application Security Project. They're typically the go-to organization for defining testing standards and classifying risks to web applications.
OWASP maintains a few different standards and helpful guides for assessment various technologies:
1. [Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/) (WSTG)
2. [Mobile Security Testing Guide](https://owasp.org/www-project-mobile-app-security/) (MSTG)
3. [Firmware Security Testing Methodology](https://github.com/scriptingxss/owasp-fstm)


## Headings by default:

# H1 For example
## H2 For example
### H3 For example
#### H4 For example
##### H5 For example
###### H6 For example

{% highlight markdown %}
## Heading first level
### Heading second level
#### Heading third level
{% endhighlight %}

***

## Lists

#### Ordered list example:

1. Poutine drinking vinegar bitters.
2. Coloring book distillery fanny pack.
3. Venmo biodiesel gentrify enamel pin meditation.
4. Jean shorts shaman listicle pickled portland.
5. Salvia mumblecore brunch iPhone migas.

{% highlight markdown %}
1. Order list item 1
2. Order list item 1
{% endhighlight %}

***

#### Unordered list example:

* Bitters semiotics vice thundercats synth.
* Literally cred narwhal bitters wayfarers.
* Kale chips chartreuse paleo tbh street art marfa.
* Mlkshk polaroid sriracha brooklyn.
* Pug you probably haven't heard of them air plant man bun.

{% highlight markdown %}
* Unordered list item 1
* Unordered list item 2
{% endhighlight %}

***

### Table

<div class="table-container">
  <table>
    <tr><th>Header 1</th><th>Header 2</th><th>Header 3</th><th>Header 4</th><th>Header 5</th></tr>
    <tr><td>Row:1 Cell:1</td><td>Row:1 Cell:2</td><td>Row:1 Cell:3</td><td>Row:1 Cell:4</td><td>Row:1 Cell:5</td></tr>
    <tr><td>Row:2 Cell:1</td><td>Row:2 Cell:2</td><td>Row:2 Cell:3</td><td>Row:2 Cell:4</td><td>Row:2 Cell:5</td></tr>
    <tr><td>Row:3 Cell:1</td><td>Row:3 Cell:2</td><td>Row:3 Cell:3</td><td>Row:3 Cell:4</td><td>Row:3 Cell:5</td></tr>
    <tr><td>Row:4 Cell:1</td><td>Row:4 Cell:2</td><td>Row:4 Cell:3</td><td>Row:4 Cell:4</td><td>Row:4 Cell:5</td></tr>
    <tr><td>Row:5 Cell:1</td><td>Row:5 Cell:2</td><td>Row:5 Cell:3</td><td>Row:5 Cell:4</td><td>Row:5 Cell:5</td></tr>
    <tr><td>Row:6 Cell:1</td><td>Row:6 Cell:2</td><td>Row:6 Cell:3</td><td>Row:6 Cell:4</td><td>Row:6 Cell:5</td></tr>
  </table>
</div>

***

## Quotes

#### A quote looks like this:

> The longer I live, the more I realize that I am never wrong about anything, and that all the pains I have so humbly taken to verify my notions have only wasted my time!
>
> <cite>George Bernard Shaw</cite>

{% highlight html %}
> The longer I live, the more I realize that I am never wrong about anything, and that all the pains I have so humbly taken to verify my notions have only wasted my time!
>
> <cite>George Bernard Shaw</cite>
{% endhighlight %}

***

## Syntax Highlighter

{% highlight js %}
  $('.top').click(function () {
    $('html, body').stop().animate({ scrollTop: 0 }, 'slow', 'swing');
  });
  $(window).scroll(function () {
    if ($(this).scrollTop() > $(window).height()) {
      $('.top').addClass("top-active");
    } else {
      $('.top').removeClass("top-active");
    };
  });
{% endhighlight %}

***

## Images

<div class="gallery-box">
  <div class="gallery">
    <img src="/images/501.jpg">
    <img src="/images/901.jpg">
    <img src="/images/509.jpg">
    <img src="/images/511.jpg">
    <img src="/images/520.jpg">
    <img src="/images/516.jpg">
    <img src="/images/517.jpg">
    <img src="/images/519.jpg">
    <img src="/images/521.jpg">
  </div>
  <em>Gallery / <a href="https://unsplash.com/" target="_blank">Unsplash</a></em>
</div>

{% highlight markdown %}
  <div class="gallery-box">
    <div class="gallery">
      <img src="/images/501.jpg">
      <img src="/images/901.jpg">
      <img src="/images/509.jpg">
      <img src="/images/511.jpg">
      <img src="/images/520.jpg">
      <img src="/images/516.jpg">
      <img src="/images/517.jpg">
      <img src="/images/519.jpg">
      <img src="/images/521.jpg">
    </div>
    <em>Gallery / <a href="https://unsplash.com/" target="_blank">Unsplash</a></em>
  </div>
{% endhighlight %}

![]({{site.baseurl}}/images/140.jpg)
*Minimalism*

{% highlight markdown %}
  ![]({{site.baseurl}}/images/140.jpg)
  *Minimalism*
{% endhighlight %}

***

## Youtube Embed

<p><iframe src="https://www.youtube.com/embed/Hd1_EXhr_fg" frameborder="0" allowfullscreen></iframe></p>

{% highlight html %}
  <iframe src="https://www.youtube.com/embed/Hd1_EXhr_fg" frameborder="0" allowfullscreen></iframe>
{% endhighlight %}

## Vimeo Embed

<p><iframe src="https://player.vimeo.com/video/107654760" width="640" height="360" frameborder="0" allowfullscreen></iframe></p>

{% highlight html %}
  <iframe src="https://player.vimeo.com/video/107654760" width="640" height="360" frameborder="0" allowfullscreen></iframe>
{% endhighlight %}

***
