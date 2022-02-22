---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: Multiple Parson's Problems on One Page
---
# Parsons Practice

## Parsons Iterative
A biologist wants you to write some code that simulates animal population growth. The code returns the population before it crashes(no more food).
<div id="itt-sortableTrash" class="sortable-code"></div> 
<div id="itt-sortable" class="sortable-code"></div> 
<div style="clear:both;"></div> 
<p> 
    <input id="itt-feedbackLink" value="Get Feedback" type="button" /> 
    <input id="itt-newInstanceLink" value="Reset Problem" type="button" /> 
</p> 
<script type="text/javascript"> 
(function(){
  var initial = "public static int populationGrowth(int food,int population)\n" +
    "    {\n" +
    "        while(food - population &gt; 0)//Does the population have enough food?\n" +
    "        {\n" +
    "        food = food - population + 2000;//Food is consumed and nature also generates food\n" +
    "        population = population * 2; //population grows AFTER food is consumed\n" +
    "        }\n" +
    "         return population;\n" +
    "    }";
  var parsonsPuzzle = new ParsonsWidget({
    "sortableId": "itt-sortable",
    "max_wrong_lines": 10,
    "grader": ParsonsWidget._graders.LineBasedGrader,
    "exec_limit": 2500,
    "can_indent": false,
    "x_indent": 0,
    "lang": "en",
    "show_feedback": true
  });
  parsonsPuzzle.init(initial);
  parsonsPuzzle.shuffleLines();
  $("#itt-newInstanceLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.shuffleLines(); 
  }); 
  $("#itt-feedbackLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.getFeedback(); 
  }); 
})(); 
</script>
## Parsons Recursive
Consider the solution above, the same thing can be done with recursion
<div id="rec-sortableTrash" class="sortable-code"></div> 
<div id="rec-sortable" class="sortable-code"></div> 
<div style="clear:both;"></div> 
<p> 
    <input id="rec-feedbackLink" value="Get Feedback" type="button" /> 
    <input id="rec-newInstanceLink" value="Reset Problem" type="button" /> 
</p> 
<script type="text/javascript"> 
(function(){
  var initial = "public static int recursivePopulation(int food, int population)\n" +
    "{\n" +
    " if(food - population &lt; 0)\n" +
    " {\n" +
    " return population;\n" +
    " }\n" +
    "return recursivePopulation(food-population+2000, population * 2);\n" +
    "}\n" +
    " if(food - population &gt; 0) #distractor\n" +
    " return recursivePopulation(food-population*2, population + 2000); #distractor\n" +
    " return population * 2; #distractor";
  var parsonsPuzzle = new ParsonsWidget({
    "sortableId": "rec-sortable",
    "max_wrong_lines": 10,
    "grader": ParsonsWidget._graders.LineBasedGrader,
    "exec_limit": 2500,
    "can_indent": false,
    "x_indent": 0,
    "lang": "en",
    "show_feedback": true,
    "trashId": "rec-sortableTrash"
  });
  parsonsPuzzle.init(initial);
  parsonsPuzzle.shuffleLines();
  $("#rec-newInstanceLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.shuffleLines(); 
  }); 
  $("#rec-feedbackLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.getFeedback(); 
  }); 
})(); 
</script>


### Implementation Notes

When you host multiple Parson's problems on a single markdown page, you need to add a unique prefix. You can easily do this in the Codio generator by typing a unique prefix into the "Prefix" textbox and pressing Enter/Return. Then you can simply copy-paste like normal.

If want each problem to be it's own page, you can use relative path links at the bottom of each of your markdown pages as seen below. If you want students to be able to return to previous problems in this format, consider adding previous links or link to a table of contents like page.

### Example Next Link
[Next](./parsons/example1.html)
