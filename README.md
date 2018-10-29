# Data processing examples
this repository aims to show examples of data processing using python. 
These examples are used in the python course developed for www.mamba-python.nl (Dutch).

#### Twitter analysis US Congres

A  [jupyter notebook](congress_twitter_analysis/congress_twitter_analysis.ipynb) with an analysis of twitter data from US congress members.
The sentiment of the tweets from US congress members is automatically analysed. 
The results are shown in a plot with the daily average sentiment for the republican and democratic party. 
Outliers are analysed and annotations are added with the cause of the outlier.

the following sources are used for this analysis:
- twitter text data from https://github.com/alexlitel/congresstweets
- twitter user data from https://github.com/alexlitel/congresstweets-automator
- polarity analysis tool from https://github.com/sloria/textblob

<figure>
   <IMG SRC="congress_twitter_analysis/figures/twitter_analysis_US_congress.png" ALIGN="left">
</figure>



#### Whatsapp data analysis
A  [jupyter notebook](/whatsapp&#32;data/whatsapp_data_analysis.ipynb) with the analysis of a whatsapp conversation.
The data was obtained by exporting a single Whatsapp chat (see https://faq.whatsapp.com/en/android/23756533/).
I did not add the full chat to this repository because of privacy issues. 
I did create an anonymised pandas dataframe that you can read to reproduce my results. 
I left the original code for the full chat so you can read you own results.


<figure>
   <IMG SRC="whatsapp data\figures\whatsapp_message_analysis.png" ALIGN="left">
</figure>

#### Groundwater modelling
A [jupyter notebook](/groundwater&#32model/groundwater_model.ipynb) with a simple groundwater model.
Metereological data was obtained from the KNMI (The Royal Netherlands Meteorological Institute).
Different years were modelled to see the differences in groundwater levels over time. 
Results are show in an animation which is shown below.


<link rel="stylesheet"
href="https://maxcdn.bootstrapcdn.com/font-awesome/4.4.0/
css/font-awesome.min.css">
<script language="javascript">
  /* Define the Animation class */
  function Animation(frames, img_id, slider_id, interval, loop_select_id){
    this.img_id = img_id;
    this.slider_id = slider_id;
    this.loop_select_id = loop_select_id;
    this.interval = interval;
    this.current_frame = 0;
    this.direction = 0;
    this.timer = null;
    this.frames = new Array(frames.length);

    for (var i=0; i<frames.length; i++)
    {
     this.frames[i] = new Image();
     this.frames[i].src = frames[i];
    }
    document.getElementById(this.slider_id).max = this.frames.length - 1;
    this.set_frame(this.current_frame);
  }

  Animation.prototype.get_loop_state = function(){
    var button_group = document[this.loop_select_id].state;
    for (var i = 0; i < button_group.length; i++) {
        var button = button_group[i];
        if (button.checked) {
            return button.value;
        }
    }
    return undefined;
  }

  Animation.prototype.set_frame = function(frame){
    this.current_frame = frame;
    document.getElementById(this.img_id).src =
            this.frames[this.current_frame].src;
    document.getElementById(this.slider_id).value = this.current_frame;
  }

  Animation.prototype.next_frame = function()
  {
    this.set_frame(Math.min(this.frames.length - 1, this.current_frame + 1));
  }

  Animation.prototype.previous_frame = function()
  {
    this.set_frame(Math.max(0, this.current_frame - 1));
  }

  Animation.prototype.first_frame = function()
  {
    this.set_frame(0);
  }

  Animation.prototype.last_frame = function()
  {
    this.set_frame(this.frames.length - 1);
  }

  Animation.prototype.slower = function()
  {
    this.interval /= 0.7;
    if(this.direction > 0){this.play_animation();}
    else if(this.direction < 0){this.reverse_animation();}
  }

  Animation.prototype.faster = function()
  {
    this.interval *= 0.7;
    if(this.direction > 0){this.play_animation();}
    else if(this.direction < 0){this.reverse_animation();}
  }

  Animation.prototype.anim_step_forward = function()
  {
    this.current_frame += 1;
    if(this.current_frame < this.frames.length){
      this.set_frame(this.current_frame);
    }else{
      var loop_state = this.get_loop_state();
      if(loop_state == "loop"){
        this.first_frame();
      }else if(loop_state == "reflect"){
        this.last_frame();
        this.reverse_animation();
      }else{
        this.pause_animation();
        this.last_frame();
      }
    }
  }

  Animation.prototype.anim_step_reverse = function()
  {
    this.current_frame -= 1;
    if(this.current_frame >= 0){
      this.set_frame(this.current_frame);
    }else{
      var loop_state = this.get_loop_state();
      if(loop_state == "loop"){
        this.last_frame();
      }else if(loop_state == "reflect"){
        this.first_frame();
        this.play_animation();
      }else{
        this.pause_animation();
        this.first_frame();
      }
    }
  }

  Animation.prototype.pause_animation = function()
  {
    this.direction = 0;
    if (this.timer){
      clearInterval(this.timer);
      this.timer = null;
    }
  }

  Animation.prototype.play_animation = function()
  {
    this.pause_animation();
    this.direction = 1;
    var t = this;
    if (!this.timer) this.timer = setInterval(function() {
        t.anim_step_forward();
    }, this.interval);
  }

  Animation.prototype.reverse_animation = function()
  {
    this.pause_animation();
    this.direction = -1;
    var t = this;
    if (!this.timer) this.timer = setInterval(function() {
        t.anim_step_reverse();
    }, this.interval);
  }
</script>

<div class="animation" align="center">
    <img id="_anim_imge04628a8c7924dd9a179ad45944fa7b3">
    <br>
    <input id="_anim_slidere04628a8c7924dd9a179ad45944fa7b3" type="range" style="width:350px"
           name="points" min="0" max="1" step="1" value="0"
           onchange="anime04628a8c7924dd9a179ad45944fa7b3.set_frame(parseInt(this.value));"></input>
    <br>
    <button onclick="anime04628a8c7924dd9a179ad45944fa7b3.slower()"><i class="fa fa-minus"></i></button>
    <button onclick="anime04628a8c7924dd9a179ad45944fa7b3.first_frame()"><i class="fa fa-fast-backward">
        </i></button>
    <button onclick="anime04628a8c7924dd9a179ad45944fa7b3.previous_frame()">
        <i class="fa fa-step-backward"></i></button>
    <button onclick="anime04628a8c7924dd9a179ad45944fa7b3.reverse_animation()">
        <i class="fa fa-play fa-flip-horizontal"></i></button>
    <button onclick="anime04628a8c7924dd9a179ad45944fa7b3.pause_animation()"><i class="fa fa-pause">
        </i></button>
    <button onclick="anime04628a8c7924dd9a179ad45944fa7b3.play_animation()"><i class="fa fa-play"></i>
        </button>
    <button onclick="anime04628a8c7924dd9a179ad45944fa7b3.next_frame()"><i class="fa fa-step-forward">
        </i></button>
    <button onclick="anime04628a8c7924dd9a179ad45944fa7b3.last_frame()"><i class="fa fa-fast-forward">
        </i></button>
    <button onclick="anime04628a8c7924dd9a179ad45944fa7b3.faster()"><i class="fa fa-plus"></i></button>
  <form action="#n" name="_anim_loop_selecte04628a8c7924dd9a179ad45944fa7b3" class="anim_control">
    <input type="radio" name="state"
           value="once" > Once </input>
    <input type="radio" name="state"
           value="loop" checked> Loop </input>
    <input type="radio" name="state"
           value="reflect" > Reflect </input>
  </form>
</div>


<script language="javascript">
  /* Instantiate the Animation class. */
  /* The IDs given should match those used in the template above. */
  (function() {
    var img_id = "_anim_imge04628a8c7924dd9a179ad45944fa7b3";
    var slider_id = "_anim_slidere04628a8c7924dd9a179ad45944fa7b3";
    var loop_select_id = "_anim_loop_selecte04628a8c7924dd9a179ad45944fa7b3";
    var frames = new Array(894);
    
  for (var i=0; i<894; i++){
    frames[i] = "plot_gws_rc_frames/frame" + ("0000000" + i).slice(-7) +
                ".png";
  }


    /* set a timeout to make sure all the above elements are created before
       the object is initialized. */
    setTimeout(function() {
        anime04628a8c7924dd9a179ad45944fa7b3 = new Animation(frames, img_id, slider_id, 33,
                                 loop_select_id);
    }, 0);
  })()
</script>

