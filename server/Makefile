postgresinit:
	docker run --name postgres17 -p 5433:5432 -e POSTGRES_USER=root -e POSTGRES_PASSWORD=password -d postgres:17.0-alpine3.20
postgres:
	docker exec -it postgres17 psql
createdb:
	docker exec -it postgres17 createdb --username=root --owner=root go-chat
dropdb:
	docker exec -it postgres17 dropdb go-chat
migrateup:
	migrate -path db/migrations -database "postgresql://root:password@localhost:5433/go-chat?sslmode=disable"
migratedown:
	migrate -path db/migrations -database "postgresql://root:password@localhost:5433/go-chat?sslmode=disable"

.PHONY: postgresinit postgres createdb dropdb migrateup migratedown