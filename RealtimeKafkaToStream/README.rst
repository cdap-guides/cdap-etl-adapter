Realtime Kafka To Stream Adapter Configuration
===============================================

The ETL Realtime Template can be used to create an Adapter that reads from a Realtime Source and persists it to a Sink.
In this example, we will read messages from Kafka in realtime and use a TableSink to write the Kafka messages to HBase.

The config.json contains a sample Adapter configuration that you can use to accomplish the above task. Our sample Adapter uses the following components:

- etlRealtime Application Template, since we want to perform ETL in realtime
- Kafka source, with our custom kafka.zookeeper configuration
- Stream sink, to write the Kafka events to a Stream

You can create and start the Adapter by using the CDAP CLI (or you can use the UI for a more visual approach).

Note: You need to fill in the ``kafka.zookeeper`` configuration in config.json before creating the Adapter.
This is the connection string to your Kafka server in ZooKeeper.

::

  cdap> create adapter kafkaIngest RealtimeTwitterToHBase/config.json
  Successfully created adapter 'KafkaIngest'

  cdap> start adapter kafkaIngest
  Successfully started adapter 'kafkaIngest'

You can verify that the data is being written to the Stream by viewing the contents of the Stream, metrics, by executing the following CLI command:

::

  cdap> get stream metrics

You have now successfully created an Adapter that reads from Kafka and writes to a Stream.

You can stop and delete the Adapter using the CDAP CLI.

::

  cdap> stop adapter kafkaIngest
  Successfully stopped adapter 'kafkaIngest'

  cdap> delete adapter kafkaIngest
  Successfully deleted adapter 'kafkaIngest'
