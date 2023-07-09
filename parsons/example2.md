---
layout: default
title: Example 2
---
<div id="sortableTrash" class="sortable-code"></div> 
<div id="sortable" class="sortable-code"></div> 
<div style="clear:both;"></div> 
<p> 
    <input id="feedbackLink" value="Get Feedback" type="button" /> 
    <input id="newInstanceLink" value="Reset Problem" type="button" /> 
</p> 
<script type="text/javascript"> 
(function(){
  var initial = "words = text.split()\n" +
    "reversed = $$toggle::&#039;&#039;::&#039; &#039;$$\n" +
    "for word in $$toggle::text::words::len(words)::range(len(words))$$:\n" +
    "reversed = $$toggle::word::reversed::words[i]$$ + $$toggle::&#039;&#039;::&#039; &#039;$$ + $$toggle::reversed::word::words[i]$$\n" +
    "reversed += $$toggle::word::words[i]::reversed$$ #distractor";
  var parsonsPuzzle = new ParsonsWidget({
    "sortableId": "sortable",
    "max_wrong_lines": 10,
    "grader": ParsonsWidget._graders.VariableCheckGrader,
    "exec_limit": 2500,
    "can_indent": true,
    "x_indent": 50,
    "lang": "en",
    "show_feedback": true,
    "trashId": "sortableTrash",
    "vartests": [
        {
            "message": "check code works for a string with no blank space",
            "initcode": "text = 'hi'",
            "code": "",
            "variables": {"reversed":"hi"}
        },
        {
            "message": "check code works for \"a short sentence\"",
            "initcode": "text = 'a short sentence'",
            "code": "",
            "variables": {"reversed":"sentence short a"}
        }
    ]
  });
  parsonsPuzzle.init(initial);
  parsonsPuzzle.shuffleLines();
  $("#newInstanceLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.shuffleLines(); 
  }); 
  $("#feedbackLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.getFeedback(); 
  }); 
})(); 
</script>
[Previous](./example1.html)
