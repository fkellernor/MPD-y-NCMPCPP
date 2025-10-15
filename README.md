# MPD y NCMPCPP

Instalación de MPD y NCMPCPP en MacBook Air M1

# Instalar Homebrew obligatorio
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Instalar MPD y NCMPCPP
brew install mpd ncmpcpp

# Una vez instalado no abrir mpd ni ncmpcpp

# Crear carpetas y archivos:
mkdir ~/.mpd
cd .mpd
mkdir playlists 
touch mpd.conf mpd.db mpd.log mpd.pid mpdstate

# Abrir con el editor de texto el archivo mpd.conf y pegar:

music_directory         "~/Music"
playlist_directory      "~/.mpd/playlists"
db_file                 "~/.mpd/mpd.db"
log_file                "~/.mpd/mpd.log"
pid_file                "~/.mpd/mpd.pid"
state_file              "~/.mpd/mpdstate"
auto_update             "yes"
auto_update_depth       "2"
follow_outside_symlinks "yes"
follow_inside_symlinks  "yes"

audio_output {
    type                  "osx"
    name                  "CoreAudio"
    mixer_type            "software"
}

decoder {
    plugin                "mp4ff"
    enabled               "no"
}

bind_to_address         "127.0.0.1"
port                    "6600"

# Visualizer
audio_output {
 type "fifo"
 name "my_fifo"
 path "/tmp/mpd.fifo"
 format "44100:16:2"
 auto_resample "no"
 use_mmap "yes"
}


