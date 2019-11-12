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
        <div id="progressBar"
             onclick="clickProgress('audioPlayer', this, event)">Pas de lecture</div>
    </div>
    <span id="progressTime">00:00</span>
</div>

<script src="js/silence.js" type="text/javascript"></script>
var player = document.querySelector('#audioPlayer');

function play(idPlayer, control) {
    var player = document.querySelector('#' + idPlayer);
	
    if (player.paused) {
        player.play();
        control.textContent = 'Pause';
    } else {
        player.pause();	
        control.textContent = 'Play';
    }
}

function resume(idPlayer) {
    var player = document.querySelector('#' + idPlayer);
	
    player.currentTime = 0;
    player.pause();
}

function volume(idPlayer, vol) {
    var player = document.querySelector('#' + idPlayer);
	
    player.volume = vol;	
}

function update(player) {
    var duration = player.duration;    // Durée totale
    var time     = player.currentTime; // Temps écoulé
    var fraction = time / duration;
    var percent  = Math.ceil(fraction * 100);

    var progress = document.querySelector('#progressBar');
	document.querySelector('#progressTime').textContent = formatTime(time);
    progress.style.width = percent + '%';
    progress.textContent = percent + '%';
}

function formatTime(time) {
    var hours = Math.floor(time / 3600);
    var mins  = Math.floor((time % 3600) / 60);
    var secs  = Math.floor(time % 60);
	
    if (secs < 10) {
        secs = "0" + secs;
    }	
    if (hours) {
        if (mins < 10) {
            mins = "0" + mins;
        }	
        return hours + ":" + mins + ":" + secs; // hh:mm:ss
    } else {
        return mins + ":" + secs; // mm:ss
    }
}

function getMousePosition(event) {
    return {
        x: event.pageX,
        y: event.pageY
    };
}

function getPosition(element){
    var top = 0, left = 0;
    
    do {
        top  += element.offsetTop;
        left += element.offsetLeft;
    } while (element = element.offsetParent);
    
    return { x: left, y: top };
}

function clickProgress(idPlayer, control, event) {
    var parent = getPosition(control);    // La position absolue de la progressBar
    var target = getMousePosition(event); // L'endroit de la progressBar où on a cliqué
    var player = document.querySelector('#' + idPlayer);
  
    var x = target.x - parent.x; 
    var wrapperWidth = document.querySelector('#progressBarControl').offsetWidth;
    
    var percent = Math.ceil((x / wrapperWidth) * 100);    
    var duration = player.duration;
    
    player.currentTime = (duration * percent) / 100;
}
</script>

</body>
</html>
