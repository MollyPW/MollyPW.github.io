---
title: "Contact Me"
permalink: "/contact/"
layout: default
---
<div class="container mt-4 mb-5">
  <h1 class="font-weight-bold title">Contact</h1>
  <form action="https://formspree.io/{{ site.email }}" method="POST">
    <p>Send me a message below and I'll reply as soon as I can!</p>
    <div class="form-group row">
      <div class="col-md-6">
        <label for="contact-name">Name*</label>
        <input class="form-control" id="contact-name" type="text" name="name" placeholder="Name*" required>
      </div>
      <div class="col-md-6">
        <label for="contact-email">E-mail Address*</label>
        <input class="form-control" id="contact-email" type="email" name="_replyto" placeholder="E-mail Address*" required>
      </div>
    </div>
    <label for="contact-message">Message*</label>
    <textarea rows="8" class="form-control mb-3" id="contact-message" name="message" placeholder="Message*" required></textarea>
    <input class="btn btn-success" type="submit" value="Send">
  </form>
</div>
