# 2021-Spotify-Analysis
CREATE TABLE BIT_DB.Spotifydata (
id integer PRIMARY KEY,
artist_name varchar NOT NULL,
track_name varchar NOT NULL,
track_id varchar NOT NULL,
popularity integer NOT NULL,
danceability decimal(4,3) NOT NULL,
energy decimal(4,3) NOT NULL,
song_key integer NOT NULL,
loudness decimal(5,3) NOT NULL,
song_mode integer NOT NULL,
speechiness decimal(5,4) NOT NULL,
acousticness decimal(6,5) NOT NULL,
instrumentalness decimal(8,7) NOT NULL,
liveness decimal(5,4) NOT NULL,
valence decimal(4,3) NOT NULL,
tempo decimal(6,3) NOT NULL,
duration_ms integer NOT NULL,
time_signature integer NOT NULL )

SELECT * FROM Spotifydata

SELECT * FROM BIT_DB.Spotifydata

--What is the average danceability by artist and track? 
SELECT avg(danceability*energy) as avg_dance, artist_name, track_name
FROM BIT_DB.Spotifydata
GROUP BY artist_name, track_name
ORDER BY avg_dance desc limit 1;

#J Balvin	Qué Más Pues?

--Who are the top 10 artists based on popularity? 

SELECT distinct artist_name
FROM BIT_DB.Spotifydata
GROUP BY artist_name, track_name
ORDER BY popularity desc limit 10;

#Ed Sheeran
#Glass Animals
#Måneskin
#The Weeknd
#The Kid LAROI
#The Neighbourhood
#Harry Styles
#Justin Bieber
#Lil Nas X
#Olivia Rodrigo

--What artist released the longest song? 

SELECT artist_name, track_name
FROM BIT_DB.Spotifydata
GROUP BY duration_ms
ORDER BY duration_ms desc limit 1;

#Farruko	Pepas

--What's the average danceability for the 10 most popular songs?

SELECT avg(danceability), artist_name, track_name, popularity
FROM BIT_DB.Spotifydata
GROUP BY popularity
ORDER BY ROUND(avg(danceability)) desc limit 10;

#0.685	Olivia Rodrigo	good 4 u	95
#0.7025	Glass Animals	Heat Waves	94
#0.63066666666667	The Weeknd	Blinding Lights	93
#0.536	Olivia Rodrigo	drivers license	92
#0.6135	Lil Nas X	MONTERO (Call Me By Your Name)	90
#0.7015	Dua Lipa	Levitating (feat. DaBaby)	89
#0.72014285714286	Doja Cat	Kiss Me More (feat. SZA)	88
#0.74725	Bad Bunny	DÁKITI	87
#0.61366666666667	Bruno Mars	Leave The Door Open	86
#0.746	The Kid LAROI	WITHOUT YOU	85
