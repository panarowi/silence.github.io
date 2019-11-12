<!DOCTYPE html>
<html lang="fr">
  <body>
    
# TITRE

## sous-titre

## VIDEO

<iframe width="560" height="315" src="https://www.youtube.com/embed/9ccV-vEiowo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



## SOUNDCLOUD

<iframe width="100%" height="50" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/472924392&color=%23212121&auto_play=false&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true&visual=true"></iframe>




## MEDIAFILE

<audio id="audioPlayer" ontimeupdate="update(this)">
    <source src="media/4 - Towers Of Nebula.mp3">
</audio>

<button class="control" onclick="play('audioPlayer', this)">Play</button>
<button class="control" onclick="resume('audioPlayer')">Stop</button>

<span class="volume">
    <a class="stick1" onclick="volume('audioPlayer', 0)"></a>
    <a class="stick2" onclick="volume('audioPlayer', 0.3)"></a>
    <a class="stick3" onclick="volume('audioPlayer', 0.5)"></a>
    <a class="stick4" onclick="volume('audioPlayer', 0.7)"></a>
    <a class="stick5" onclick="volume('audioPlayer', 1)"></a>
</span>

<div>
    <div id="progressBarControl">
        <div id="progressBar">Pas de lecture</div>
    </div>
</div>

<script src="./js/silence.js" type="text/javascript"></script>

</body>
</html>
