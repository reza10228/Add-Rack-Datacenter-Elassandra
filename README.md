# Add Rack Datacenter Elassandra

**Step 1**

**Run On DC1**

`ALTER KEYSPACE "mediana_sms" WITH replication = {'class': 'NetworkTopologyStrategy' , 'DC1': 1 , 'DC2': 0 } ;`

**Run On DC1**

```
ALTER KEYSPACE system_auth WITH REPLICATION =
  {'class' : 'NetworkTopologyStrategy', 'DC1' : 1, 'DC2' : 1};
```

**Step 2**

**On New DataCenter**

`nodetool rebuild -- DC1`

**Cammand Check Status**

`nodetool netstats`
`nodetool  gossipinfo`

**Sample Cammand on Elassandra**

##### DROP KEYSPACE

`DROP KEYSPACE sms ;`


##### DROP TABLE

`DROP TABLE  sms.send ;`

##### Show KEYSPACE

`SELECT * FROM system_schema.tables WHERE keyspace_name = 'sms' ;`

`SELECT * FROM system_schema.keyspaces;`

##### Truncate Tabels
`TRUNCATE sms.send;`

`DESC mediana_sms.send`


`SELECT * FROM sms.send LIMIT 1 ;`

`SELECT * FROM sms.send WHERE id=1 ;`

`INSERT INTO sms.send (id , "to" , "from" , user_id  ) VALUES ( 1 , '09193211002' , '3000003030303' , '123456' ) ;`
