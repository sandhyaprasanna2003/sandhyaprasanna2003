<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Music Player</title>
  <style>
    /* CSS Styles */
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
    }
    .container {
      max-width: 800px;
      margin: 20px auto;
      padding: 20px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    h1 {
      text-align: center;
    }
    audio {
      width: 100%;
      margin: 10px 0;
    }
    .controls {
      display: flex;
      justify-content: center;
      align-items: center;
      margin-top: 20px;
    }
    .controls button {
      margin: 0 10px;
      font-size: 20px;
      cursor: pointer;
    }
    .playlist {
      list-style: none;
      padding: 0;
    }
    .playlist li {
      margin-bottom: 10px;
    }
    .playlist img {
      width: 50px;
      height: 50px;
      margin-right: 10px;
      vertical-align: middle;
    }
    .progress {
      width: 100%;
      height: 10px;
      background-color: #ccc;
      margin-top: 10px;
    }
    .progress-bar {
      height: 100%;
      background-color: #4CAF50;
    }
    .search-input {
      width: 100%;
      padding: 10px;
      margin-bottom: 10px;
      box-sizing: border-box;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Music Player</h1>
    <input type="text" id="searchInput" class="search-input" placeholder="Search for songs...">
    <audio id="audio" controls></audio>
    <div class="controls">
      <button id="prevBtn">&lt;&lt;</button>
      <button id="playBtn">&#9658;</button>
      <button id="nextBtn">&gt;&gt;</button>
      <button id="shuffleBtn">Shuffle</button>
      <button id="repeatBtn">Repeat</button>
      <button id="downloadBtn" disabled>Download</button>
      <input type="range" id="volumeSlider" min="0" max="1" step="0.1" value="1">
    </div>
    <ul class="playlist" id="playlist"></ul>
    <div class="progress">
      <div class="progress-bar" id="progressBar"></div>
    </div>
  </div>

  <script>
    // JavaScript code
    const audio = document.getElementById('audio');
    const playBtn = document.getElementById('playBtn');
    const prevBtn = document.getElementById('prevBtn');
    const nextBtn = document.getElementById('nextBtn');
    const shuffleBtn = document.getElementById('shuffleBtn');
    const repeatBtn = document.getElementById('repeatBtn');
    const downloadBtn = document.getElementById('downloadBtn');
    const volumeSlider = document.getElementById('volumeSlider');
    const progressBar = document.getElementById('progressBar');
    const playlist = document.getElementById('playlist');
    const searchInput = document.getElementById('searchInput');

    let currentTrackIndex = 0;
    let isPlaying = false;
    let isShuffle = false;
    let isRepeat = false;

    const tracks = [
      { name: 'Song 1', artist: 'Artist 1', src: 'song1.mp3', cover: 'cover1.jpg' },
      { name: 'Song 2', artist: 'Artist 2', src: 'song2.mp3', cover: 'cover2.jpg' },
      // Add more songs here
    ];

    function loadTrack(trackIndex) {
      const track = tracks[trackIndex];
      audio.src = track.src;
      audio.play();
      document.title = `${track.name} - ${track.artist}`;
      isPlaying = true;
      playBtn.textContent = '❚❚';
      downloadBtn.href = track.src;
      downloadBtn.removeAttribute('disabled');
    }

    function playPause() {
      if (isPlaying) {
        audio.pause();
        isPlaying = false;
        playBtn.textContent = '&#9658;';
      } else {
        audio.play();
        isPlaying = true;
        playBtn.textContent = '❚❚';
      }
    }

    function nextTrack() {
      if (isShuffle) {
        currentTrackIndex = Math.floor(Math.random() * tracks.length);
      } else {
        currentTrackIndex = (currentTrackIndex + 1) % tracks.length;
      }
      loadTrack(currentTrackIndex);
    }

    function prevTrack() {
      currentTrackIndex = (currentTrackIndex - 1 + tracks.length) % tracks.length;
      loadTrack(currentTrackIndex);
    }

    function shuffleTracks() {
      isShuffle = !isShuffle;
      shuffleBtn.textContent = isShuffle ? 'Shuffle (On)' : 'Shuffle';
    }

    function repeatTracks() {
      isRepeat = !isRepeat;
      repeatBtn.textContent = isRepeat ? 'Repeat (On)' : 'Repeat';
    }

    function updateProgressBar() {
      const progress = (audio.currentTime / audio.duration) * 100;
      progressBar.style.width = `${progress}%`;
    }

    function setVolume() {
      audio.volume = volumeSlider.value;
    }

    function searchSongs() {
      const query = searchInput.value.trim();
      if (query !== '') {
        // Perform Google search or Chrome search for songs
        window.open(`https://www.google.com/search?q=${query} songs`, '_blank');
      }
    }

    audio.addEventListener('timeupdate', updateProgressBar);
    audio.addEventListener('ended', () => {
      if (isRepeat) {
        audio.currentTime = 0;
        audio.play();
      } else {
        nextTrack();
      }
    });
    playBtn.addEventListener('click', playPause);
    prevBtn.addEventListener('click', prevTrack);
    nextBtn.addEventListener('click', nextTrack);
    shuffleBtn.addEventListener('click', shuffleTracks);
    repeatBtn.addEventListener('click', repeatTracks);
    volumeSlider.addEventListener('input', setVolume);
    searchInput.addEventListener('keydown', (e) => {
      if (e.key === 'Enter') {
        searchSongs();
      }
    });

    // Populate playlist
    tracks.forEach((track, index) => {
      const listItem = document.createElement('li');
      listItem.innerHTML = `<img src="${track.cover}" alt="${track.name}"><span>${track.name} - ${track.artist}</span>`;
      listItem.addEventListener('click', () => {
        currentTrackIndex = index;
        loadTrack(currentTrackIndex);
      });
      playlist.appendChild(listItem);
    });

    // Load first track
    loadTrack(currentTrackIndex);
  </script>
</body>
</html>
