# Collin

Go to https://www.mlive.com/expo/sports/erry-2018/09/80f7ed1f231855/vote-for-ann-arborarea-high-sc.html 
Make sure the poll loads 
Right click anywhere on the page (Control-Click on Macs) 
Click inspect element 
Click on console 
Copy and paste this code in and press enter:

document.onkeypress = function(e) {
    if(e.keyCode === 13) //if enter pressed
    {
        eventFire(vote_btn, 'click');
    }
};
function select() {
    radio = document.getElementById('PDI_answer46373917');
    vote_btn = document.getElementById('pd-vote-button10103413');
    back_btn = document.querySelector('.pds-return-poll');
}

function eventFire(el, etype) {
    if (el.fireEvent) {
        el.fireEvent('on' + etype);
    } else {
        var evObj = document.createEvent('Events');
        evObj.initEvent(etype, true, false);
        evObj.which = el;
        i = i + 1;
        el.dispatchEvent(evObj);
    }
}
function sleep(miliseconds) {
    var currentTime = new Date().getTime();
    while (currentTime + miliseconds >= new Date().getTime()) {
    }
}

i = 0;
setInterval(function () {
    //if (i == 25) {
    //    sleep(120000);
    //    i = 0;
    //}
    //console.log(i);
    select();
    try {
        radio.click();
        eventFire(vote_btn, 'click');
    } catch (e) { }
}, 3000);
setInterval(function () {
    select();
    try { back_btn.click(); } catch (e) { }
}, 7500, 7500);
