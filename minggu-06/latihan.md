## Install Go, MongoDb dan MySql
![1](gambar-01)

## Program Go MySQL
```
Mohon maaf disini dbms MySQL saya sedikit bermasalah di MX linux, sebagai alternatif saya menggantinya dengan PostgreSQL
```

```
package main

import (
	"database/sql"
	"fmt"
	"log"

	_ "github.com/lib/pq"
)

func main() {
	db, err := sql.Open("postgres", "user=akbar password=01111997 dbname=latihan sslmode=disable")
	if err != nil {
		log.Fatal(err)
	}
	defer db.Close()

	err = db.Ping()
	if err != nil {
		log.Fatal(err)
	}

	rows, err := db.Query("SELECT nim, nama FROM mahasiswa")
	if err != nil {
		log.Fatal(err)
	}
	defer rows.Close()

	for rows.Next() {
		var nim string
		var nama string
		if err := rows.Scan(&nim, &nama); err != nil {
			log.Fatal(err)
		}
		fmt.Printf("NIM: %s, Nama: %s\n", nim, nama)
	}

	if err := rows.Err(); err != nil {
		log.Fatal(err)
	}
}
```
### Output

![1](gambar-02.png)

## Program Go MongoDB

```
package main

import (
	"context"
	"fmt"
	"log"

	"go.mongodb.org/mongo-driver/bson"
	"go.mongodb.org/mongo-driver/mongo"
	"go.mongodb.org/mongo-driver/mongo/options"
)

func main() {
	clientOptions := options.Client().ApplyURI("mongodb://localhost:27017")
	client, err := mongo.Connect(context.TODO(), clientOptions)
	if err != nil {
		log.Fatal(err)
	}
	defer client.Disconnect(context.TODO())

	collection := client.Database("latihan").Collection("mahasiswa")

	filter := bson.D{}

	cursor, err := collection.Find(context.TODO(), filter)
	if err != nil {
		log.Fatal(err)
	}
	defer cursor.Close(context.TODO())

	for cursor.Next(context.TODO()) {
		var result bson.M
		err := cursor.Decode(&result)
		if err != nil {
			log.Fatal(err)
		}
		fmt.Println(result)
	}

	if err := cursor.Err(); err != nil {
		log.Fatal(err)
	}
}
```

### Output
![1](gambar-03.png)
