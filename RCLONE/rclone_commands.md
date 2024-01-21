rclone commands
========================

#### get names of remotes
rclone listremotes

#### list files in dir of remote
rclone lsd "one drive:Pictures"

#### clone from specified local dir to remote dir on MS One Drive
rclone sync /home/source/dir "one drive:dest_dir" -v