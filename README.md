# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
(first only) docker exec -it demo-arclight-arclightsolr-1 solr create_core -c arclight
docker cp solr/managed-schema.xml demo-arclight-arclightsolr-1:/var/solr/data/arclight/conf/managed-schema.xml
docker compose up --force-recreate

docker exec -it demo-arclight-arclight-1 bash
FILE=eads/1.xml REPOSITORY_ID=InU-aaamc bundle exec rake arclight:index
FILE=eads/2.xml REPOSITORY_ID=InU-aaamc bundle exec rake arclight:index
FILE=eads/3.xml REPOSITORY_ID=InU-aaamc bundle exec rake arclight:index

docker compose build --no-cache && docker compose up --force-recreate

stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
docker volume rm demo-arclight_data