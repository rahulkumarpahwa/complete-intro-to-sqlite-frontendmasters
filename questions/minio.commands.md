1. start the minio server with docker 
docker run -p 9000:9000 -p 9001:9001 minio/minio server /data --console-address ":9001"

2. docker command to open mc minio client using its shell sh
   docker exec -it 'container-name' sh

In shell-

3. check the list of alias 'short form for the connection URL' name available.
   mc alias list

4. set the accesskey and secret key for the alias 'short form for the connection URL'. for local experiment, make this same as admin login and password
   mc alias set local http://localhost:9000 minioadmin minioadmin

  - create the bucket in the UI of your choice of name.

5. set your access permission for your bucket as 'here the name of the my bucket is chinook-backup'
   mc anonymous set public local/chinook-backup
