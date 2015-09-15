var barSize, vid, playBtn, defBar, progBar, updateBar, _time, ex, playMe, nav, _durTime, skin,
volAdjust, vol, volControl, eng, sub, caption;

function doFirst() {
    vid = document.getElementById('vid');
    playBtn = document.getElementById('playBtn');
    defBar = document.getElementById('defaultBar');
    progBar = document.getElementById('progBar');
    _time = document.getElementById('_time');
    ex = document.getElementById('ex');
    playMe = document.getElementById('playMe');
    nav = document.getElementById('nav');
    _durTime = document.getElementById('_durTime');
    skin = document.getElementById('skin');
    volAdjust = document.getElementById('volAdjust');
    vol = document.getElementById('volWrap');
    volControl = document.getElementById('volControl');
    eng = document.getElementById('eng');
    sub = document.getElementById('sub');
    caption = document.getElementById('caption');
    barSize = (defBar.clientWidth);

    
    playBtn.addEventListener('click', playOrPause, false);
    defBar.addEventListener('click', clickedBar, false);
    playMe.addEventListener('click', playMeFunc, false);

    ex.addEventListener('click', toggleFullscreen, false);
    volControl.addEventListener('click', volCont, false);

    // Loading Video
vid.addEventListener('canplay', function() {  
console.log("Playing...");
});

    fullDurTime();
}


function update() {
    if(!vid.ended) {
        var size = parseInt(vid.currentTime * barSize/vid.duration);
        progBar.style.width = size + 'px';
        
        // Time Duration
        var curMin = Math.floor(vid.currentTime / 60);
        var curSec = Math.floor(vid.currentTime - curMin * 60);
        if(curMin < 10) {
            _time.innerHTML = "0" + curMin + ":" + curSec;
        }
        if(curSec < 10) {
            _time.innerHTML = curMin + ":0" + curSec;
        }
        if(curMin < 10 && curSec < 10) {
            _time.innerHTML = "0" + curMin + ":0" + curSec;
        }
        if(curMin >= 10 && curSec >= 10) {
            _time.innerHTML = curMin + ":" + curSec;
        }
    }else {
        playBtn.src = 'skin/img/play.png';
        progBar.style.width = '0px';
        playMe.src = 'skin/img/reload.png';
        playMe.style.display = 'initial';
        _time.innerHTML = '00:00';
        window.clearInterval(updateBar);
    }
}

function playOrPause() {
    if(!vid.paused && !vid.ended) {
        vid.pause();
        playBtn.src = 'skin/img/play.png';
        playMe.src = 'skin/img/playMe.png';
        playMe.style.display = 'initial';
        window.clearInterval(updateBar);
    }else {
        vid.play();
        playBtn.src = 'skin/img/pause.png';
        playMe.style.display = 'none';
        updateBar = setInterval(update, 1000);
    }
//alert(barSize);
}
function playMeFunc() {
    playOrPause();
}

var isOk = true;
function toggleFullscreen() {
    if (vid.requestFullscreen) {
      vid.requestFullscreen();
      nav.style.zIndex = '2147483647';
    } else if (vid.msRequestFullscreen) {
      vid.msRequestFullscreen();
      nav.style.zIndex = '2147483647';
    } else if (vid.mozRequestFullScreen) {
      vid.mozRequestFullScreen();
      nav.style.zIndex = '2147483647';
    } else if (vid.webkitRequestFullscreen) {
      vid.webkitRequestFullscreen();
      nav.style.zIndex = '2147483647';
    }else {
        vid.exitFullscreen();
        vid.mozCancelFullScreen();
        vid.webkitExitFullscreen();
        vid.msExitFullscreen();
    }
    if(isOk){
        skin.style.height = '100vh';
        skin.style.width = '100%';
        nav.style.bottom = '-90vh';
        nav.style.width = '100%';
        defBar.style.width = '60em';
        isOk = false;
    }else {
        isOk = true;
    }
}


// full duration time
function fullDurTime() {
    var durMin = Math.floor(vid.duration / 60);
    var durSec = Math.floor(vid.duration - durMin * 60);

    if(durMin < 10) {
        _durTime.innerHTML = "0" + durMin + ":" + durSec;
    }
    if(durSec < 10) {
        _durTime.innerHTML = durMin + ":0" + durSec;
    }
    if(durMin < 10 && durSec < 10) {
        _durTime.innerHTML = "0" + durMin + ":0" + durSec;
    }
    if(durMin >= 10 && durSec >= 10) {
        _durTime.innerHTML = durMin + ":" + durSec;
    }
}



// Volume Function
function volCont(ev) {
if(isOk) {
     volBarSize = volControl.clientHeight;
    // var curVol = vid.volume;
    vid.volume = 1.0;
    var mouseY = vid.clientHeight - (ev.pageY - volControl.offsetTop) - 25;
    //mouseY -= 460;
    //mouseY = -mouseY;
    var newVolume = mouseY * vid.volume / volBarSize;
    vid.volume = parseFloat(newVolume);
    volAdjust.style.height = mouseY + 'px';
//alert(volBarSize);
}else {
    volBarSize = volControl.clientHeight;
    // var curVol = vid.volume;
    vid.volume = 1.0;
    var mouseY = screen.clientHeight - (ev.pageY - volControl.offsetTop) - 25;
    //mouseY -= 460;
    //mouseY = -mouseY;
    var newVolume = mouseY * vid.volume / volBarSize;
    vid.volume = parseFloat(newVolume);
    volAdjust.style.height = mouseY + 'px';
}
}





//  clickeBar function 
function clickedBar(e) {
    //skin width
    var skinWidth = screen.width - skin.clientWidth;
    //screen.width = screen.width - skinWidth;
    barSize = (defBar.clientWidth);
    if(isOk) {
        if(!vid.paused && !vid.ended) {
            var mouseX = (e.pageX - defBar.offsetLeft);
            var newTime = mouseX * vid.duration / barSize;
            //newTime -= parseInt(vid.duration/4); // I dont know how this working
            vid.currentTime = newTime;
            mouseX -= screen.width - skinWidth; // I dont know how this working
            progBar.style.width = mouseX + 'px';
        }
    }else {
        if(!vid.paused && !vid.ended) {
            var mouseX = (e.pageX - defBar.offsetLeft);
            var newTime = mouseX * vid.duration / barSize;
            vid.currentTime = newTime;
            progBar.style.width = mouseX + 'px';
        }
    }
   alert(mouseX);
}



// addSubTitle function




// Resize Method
function usrResize() {
   defBar.style.width = screen.clientWidth - 100 + "px";
}



window.addEventListener('load', doFirst, false);
