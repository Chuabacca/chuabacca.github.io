---
layout: post
title: "HTML Email"
date:   2015-10-28 08:53:30
category: CS, Frontend
author: Jonathan Chua
comments: true
image: email.jpg
---

Recently, I’ve been learning how to write HTML emails from scratch. In many ways it like taking a trip back to 1999. Are you ready for it? HTML email are built with tables… OK, you can pick your jaw up off the floor now. Actually it’s not so bad. Working in a constrained environment is the perfect condition to stimulate creativity. Of course, there are some pretty significant pain points, but the bigger the pain, the more awesome the workaround.

# The Basics
You can think of an HTML email as a self-contained webpage that gets rendered in an email client. There are several different email clients out there, and each one will treat your code differently. The lack of standards across email clients accounts for most of the pain that one might experience in writing HTML emails. Here are the latest email client market share statistics from [emailclientmarketshare.com][ECMS] produced by Litmus.
<ol>
<li>Apple iPhone - 29%</li>
<li>Gmail - 16%</li>
<li>Apple iPad - 11%</li>
<li>Google Android - 9%</li>
<li>Apple Mail - 8%</li>
<li>Outlook - 8%</li>
<li>Outlook.com - 4%</li>
<li>Yahoo! Mail - 3%</li>
<li>Windows Live Mail - 2%</li>
<li>Windows Mail - 1%</li>
</ol>
When you send your email to these clients, all you get is one file. That means no external style sheets. You can’t even rely on keeping your styles in a <styles> tag since some email clients strip that out. All your styles must be inline.

# Getting Started
If your head hasn’t exploded yet, let’s go on to writing the actual code. Many tutorials recommend that you start out with this doctype declaration and html tag:
{% highlight html %}
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
{% endhighlight %}
Some say that this produces the most stable results. In my experience, it hasn’t made a difference. So I stick with the cleaner markup that is used by the guys at Litmus.
{% highlight html %}
<!doctype html>
<html>
{% endhighlight %}
If anything, it just a mental/personal preference thing. Using the standard HTML5 markup helps me feel like I’m living in the 21st century. =)

# Get Modular
I mentioned that HTML emails are built with tables. If you are imagining endless lines of nested tags, you aren’t far off. You can get so deep into the nesting that you end up in [limbo][inception], and you’ll never find your way out. You can keep your sanity and minimize nesting by making the design of your email modular. That means each section of the email will be in its own table instead of having one big table and sticking everything inside of it. Here’s what a modular table looks like.
{% highlight html %}
<table align="center" border="0" cellspacing="0" cellpadding=“0”>
<tr>
	<td style=“…”>
		<table align="center" border="0" cellspacing="0" cellpadding=“0”>
			…
		</table>
	</td>
</tr>
</table>
{% endhighlight %}
This is the framework that I start off with when I design an email. When one section is complete, I start with a new table and stick it right below the first one. 

Notice the html attributes in the table tag. This helps to ensure that email clients don’t render any of the default table styles like borders or add any extra padding to the design. Yes, it must be added to every table tag. 

Also, a style attribute is added to the table cell tag. This is where most of the styling takes place. But, if a valid HTML atribute exists to do the thing you want, use that instead of a CSS style. Since some clients ignore margins, positioning elements must be done with padding instead. And because padding is on the inside of the cell, that means nesting another table inside of it to create the layout you want. 

# Want to Learn More?
There is a lot more to HTML email. This just barely scratches the surface. If you’d like to learn more, these are the resources that got me to where I am today. Check out the links below.

[Unmasking HTML Email Tutorial: CodeSchool][CS] - This is the best tutorial on HTML email that I’ve found.

[Soup to Bits: HTML Email][soup] - In this screen cast, Dan Denny from Code School teams up with Kevin Madeville to create an email infront of your very eyes!

[HTML Email Design: Treehouse] - This is a pretty good introduction to designing HTML emails.

[MailChimp HTML Email Development Reference][MC] - This super-helpful site covers the various aspects of HTML email. It's a great place to go to look things up.

[Free Evato Tutorial][webdesign] - This is a pretty cool tutorial site that walks you through the creation of a responsive email.



[ECMS]: https://emailclientmarketshare.com
[inception]: http://www.imdb.com/title/tt1375666/
[CS]: https://www.codeschool.com/courses/unmasking-html-emails
[soup]: https://www.codeschool.com/screencasts/soup-to-bits-unmasking-html-emails
[MC]: http://templates.mailchimp.com/development/
[webdesign]: http://webdesign.tutsplus.com/articles/creating-a-simple-responsive-html-email--webdesign-12978
