
# vjstat

A simple python script to visualise the JVM heap of a process in real-time from the output of [jstat]( http://docs.oracle.com/javase/1.5.0/docs/tooldocs/share/jstat.html)

Input can be from stdin or a [0mq](http://zeromq.org) socket.  [Pyqtgraph](http://www.pyqtgraph.org/) is used for visualisation.


## Examples

1.  Pipe the output of jstat directly to the script:

    ```bash
    jstat -gc $(jps <jvm-process-name>) 100ms | vjstat -i 100 -w 10000
    ```

2.  Connect to a 0mq socket where the output of `jstat` is being published:

    ```bash
    jstat -gc $(jps <jvm-process-name) 1s | zmqpp pub 'tcp://*:4242'
    ```

    ```bash
    vjstat -i 1000 tcp://<host>:4242
    ```

[Sample output](./sample.svg)

