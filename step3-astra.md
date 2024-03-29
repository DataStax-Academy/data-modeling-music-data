<!-- TOP -->
<div class="top">
  <img class="scenario-academy-logo" src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-2023.svg" />
  <div class="scenario-title-section">
    <span class="scenario-title">Digital Library Data Modeling</span>
    <span class="scenario-subtitle">ℹ️ For technical support, please contact us via <a href="mailto:aleksandr.volochnev@datastax.com">email</a> or <a href="https://dtsx.io/aleks">LinkedIn</a>.</span>
  </div>
</div>

<!-- NAVIGATION -->
<div id="navigation-top" class="navigation-top">
 <a href='command:katapod.loadPage?[{"step":"step2-astra"}]' 
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 3 of 13</span>
 <a href='command:katapod.loadPage?[{"step":"step4-astra"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Populate tables using DSBulk</div>

✅ Load data into table `performers`:
```
astra db load data-modeling             \
            -url assets/performers.csv  \
            -k music_data               \
            -t performers               \
            -header true                \
            -logDir /tmp/logs
```

✅ Retrieve some rows from table `performers`:
```
astra db cqlsh data-modeling -e "SELECT * FROM music_data.performers LIMIT 10;"      
```

✅ Load data into tables `albums_by_performer`, `albums_by_title` and `albums_by_genre`:
```
astra db load data-modeling             \
            -url assets/albums.csv      \
            -k music_data               \
            -t albums_by_performer      \
            -header true                \
            -logDir /tmp/logs

astra db load data-modeling             \
            -url assets/albums.csv      \
            -k music_data               \
            -t albums_by_title          \
            -header true                \
            -logDir /tmp/logs

astra db load data-modeling             \
            -url assets/albums.csv      \
            -k music_data               \
            -t albums_by_genre          \
            -header true                \
            -logDir /tmp/logs
```

✅ Retrieve some rows from tables `albums_by_performer`, `albums_by_title` and `albums_by_genre`:
```
astra db cqlsh data-modeling -e "SELECT * FROM music_data.albums_by_performer LIMIT 5;"   
astra db cqlsh data-modeling -e "SELECT * FROM music_data.albums_by_title LIMIT 5;"   
astra db cqlsh data-modeling -e "SELECT * FROM music_data.albums_by_genre LIMIT 5;"                                       
```

✅ Load data into tables `tracks_by_title` and `tracks_by_album`:
```
astra db load data-modeling             \
            -url assets/tracks.csv      \
            -k music_data               \
            -t tracks_by_title          \
            -header true                \
            -m "0=album_title,          \
                1=album_year,           \
                2=genre,                \
                3=number,               \
                4=title"                \
            -logDir /tmp/logs

astra db load data-modeling             \
            -url assets/tracks.csv      \
            -k music_data               \
            -t tracks_by_album          \
            -header true                \
            -m "0=album_title,          \
                1=album_year,           \
                2=genre,                \
                3=number,               \
                4=title"                \
            -logDir /tmp/logs
```

✅ Retrieve some rows from tables `tracks_by_title` and `tracks_by_album`:
```
astra db cqlsh data-modeling -e "SELECT * FROM music_data.tracks_by_title LIMIT 5;"   
astra db cqlsh data-modeling -e "SELECT * FROM music_data.tracks_by_album LIMIT 5;"      
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step2-astra"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step4-astra"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
