---
layout: post
title:  "A Rather Natural Approach to Understanding the Artificial Neuron"
date:   2018-06-21 00:00:00 +0530
categories: deep-learning
---

Hello there, welcome to the Rising-Star Exhibition Center. I hope you are well acquainted with the drill. Well, it never hurts to repeat the instructions so hear me out:

Before you're allowed to enter, you have to pass a very simple aptitude test. We will show you two stones. Study them carefully. Pay particular attention to their **shape**, **color** and **roughness**. You're free to take as much time as you may require. After you are done studying the two stones, we will show you another sample which belong to one of the stones you just studied. All you need to do, is tell us which of the previous stones you studied does this stone belong to.

Do you have any questions? [After a minute passes] Well, thank you.

Now, shall we begin? Take a closer look at these marvelous stones, would you?

![Stone A and B](/assets/img/perceptron/train.png "Stone A and B")

Great. Now that you're done examining them. Can you tell us whether this stone is of type A or B?

![Stone Test](/assets/img/perceptron/A_test.png "Stone Test")
<span>
<button class="button btn-yes" id="correct-btn">Stone A</button>
<button class="button btn-no" id="incorrect-btn">Stone B</button>
</span>

<div id="correct">
Well done, come in please.
</div>

<div id="incorrect">
 Wrong!
</div>

---

<br><br>

## Identifying differences

Now, let's go through the process of learning to see differences between two objects and using that to identify future objects.

<style>
.button {
  position: relative;
  display: inline-block;
  margin: 2rem 1rem;
  height: 2rem;
  /* padding: 0; */
  overflow: hidden;
  border-width: 0;
  outline: none;
  border-radius: 2px;
  box-shadow: 0 1px 4px rgba(0, 0, 0, .6);
  color: #ecf0f1;
  transition: background-color .3s;
  cursor: pointer;
}

.btn-yes {
  background-color: #7e57c2;
}

.btn-no {
  background-color: #3f51b5;
}

.is-hidden {
  display: none;
}
</style>

<script type="text/javascript">
var correctDiv = document.getElementById('correct');
var inCorrectDiv = document.getElementById('incorrect');

var correctBtn = document.getElementById('correct-btn');
var inCorrectBtn = document.getElementById('incorrect-btn');

correctDiv.classList.add('is-hidden');
inCorrectDiv.classList.add('is-hidden');

correctBtn.addEventListener('click', function () {
  correctDiv.classList.remove('is-hidden');
  inCorrectDiv.classList.add('is-hidden');
});


inCorrectBtn.addEventListener('click', function () {
  inCorrectDiv.classList.remove('is-hidden');
  correctDiv.classList.add('is-hidden');
});


</script>