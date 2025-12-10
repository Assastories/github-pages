<style>
#player-container {
    position: fixed !important;
    top: 0;
    left: 0;
    width: 100vw !important;
    height: 100vh !important;
    margin: 0 !important;
    padding: 0 !important;
    background: #000;
    z-index: 999999;
}

#player-container iframe {
    width: 100%;
    height: 100%;
    border: none !important;
}
</style>

<div id="player-container">
    <iframe id="safe-player"
        sandbox="allow-same-origin allow-scripts allow-forms allow-presentation"
        referrerpolicy="no-referrer"
        allowfullscreen></iframe>
</div>

<script>
let videoURL = "https://9xplayer.com/?url=https://www.facebook.com/61558144589944/videos/681236357891563/?mibextid=Nif5oz";

window.addEventListener("load", function() {
    document.getElementById("safe-player").src = videoURL;
});
</script>
