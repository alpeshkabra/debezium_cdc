# Start the application
docker compose up --build

# Connect mysql sql sink connector
curl -i -X POST -H "Accept:application/json" -H  "Content-Type:application/json" http://localhost:8083/connectors/ -d @jdbc-mysql-sink.json

# Connect sql server sink connector
curl -i -X POST -H "Accept:application/json" -H  "Content-Type:application/json" http://localhost:8083/connectors/ -d @jdbc-sql-server-sink.json

# Connect sql server source connector
curl -i -X POST -H "Accept:application/json" -H  "Content-Type:application/json" http://localhost:8083/connectors/ -d @sql-server-source.json
```

# Connect mysql source connector
curl -i -X POST -H "Accept:application/json" -H  "Content-Type:application/json" http://localhost:8083/connectors/ -d @mysql-source.json
```

# Update sql server db
/opt/mssql-tools/bin/sqlcmd -U sa -P Password! -i /tmp/debezium-sqlserver-init/inventory.sql

# Command to delete Connector
curl -i -X DELETE localhost:8083/connectors/mysql-sink
curl -i -X DELETE localhost:8083/connectors/sql-server-sink
curl -i -X DELETE localhost:8083/connectors/mysql-connector
curl -i -X DELETE localhost:8083/connectors/sql-server-connector