
< script  src = " https://apis.google.com/js/api.js " > </ script >
< script >
  fungsi  otentikasi () {
    kembali  gapi . auth2 . getAuthInstance ()
        . masuk ({scope :  " https://www.googleapis.com/auth/yt-analytics.readonly " })
        . lalu ( function () { console . log ( " Berhasil masuk " );},
              function ( err ) { console . kesalahan ( " Kesalahan saat masuk " , err); });
  }
  function  loadClient () {
    kembali  gapi . klien . memuat ( " https://youtubeanalytics.googleapis.com/$discovery/rest?version=v2 " )
        . lalu ( function () { console . log ( " klien GAPI dimuat untuk API " );},
              function ( err ) { console . error ( " Kesalahan memuat klien GAPI untuk API " , err); });
  }
  // Pastikan klien dimuat dan proses masuk selesai sebelum memanggil metode ini.
  function  execute () {
    kembali  gapi . klien . youtubeAnalytics . laporan . permintaan ({
      " ids " :  " channel == MINE " ,
      " startDate " :  " 2017-01-01 " ,
      " endDate " :  " 2017-12-31 " ,
      " metrik " :  " tampilan, estimasiMinutesWatched, averageViewDuration, averageViewPercentage, pelangganDapatkan " ,
      " dimensi " :  " hari " ,
      " sort " :  " day "
    })
        . then ( function ( response ) {
                // Tangani hasilnya di sini (response.result memiliki tubuh yang diuraikan).
                konsol . log ( " Respons " , respons);
              },
              function ( err ) { console . error ( " Execute error " , err); });
  }
  gapi . memuat ( " klien: auth2 " , function () {
    gapi . auth2 . init ({client_id :  ' YOUR_CLIENT_ID ' });
  });
</ skrip >
< tombol  onclick = " otentikasi (). lalu (loadClient) " > otorisasi dan muat </ tombol >
< tombol  onclick = " eksekusi () " > jalankan </ tombol >
