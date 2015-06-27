You need:
* vagrant >= 1.7.0
* virtualbox

1. ``git clone https://github.com/bechtoldt/salt-debug-24440.git --recursive``
2. ``cd salt-debug-24440/vagrant``
3. ``vagrant up`` (will take ~ 5 mins)
4. ``vagrant ssh``
5. ``sudo -i``
6. ``systemctl stop salt-minion``
7. ``salt-minion -l trace``


::

    # salt-minion -l trace
    [DEBUG   ] Reading configuration from /etc/salt/minion
    [DEBUG   ] Using cached minion ID from /etc/salt/minion_id: client1.elasticsearch.local.arnoldbechtoldt.com
    [TRACE   ] None of the required configuration sections, 'logstash_udp_handler' and 'logstash_zmq_handler', were found the in the configuration. Not loading the Logstash logging handlers module.
    [TRACE   ] The required configuration section, 'fluent_handler', was not found the in the configuration. Not loading the fluent logging handlers module.
    [DEBUG   ] Configuration file path: /etc/salt/minion
    [TRACE   ] Trying pysss.getgrouplist for 'root'
    [TRACE   ] Trying generic group list for 'root'
    [TRACE   ] Group list for user 'root': []
    [INFO    ] Setting up the Salt Minion "client1.elasticsearch.local.arnoldbechtoldt.com"
    [DEBUG   ] Created pidfile: /var/run/salt-minion.pid
    [DEBUG   ] Reading configuration from /etc/salt/minion
    [TRACE   ] Loading core.hwaddr_interfaces grain
    [TRACE   ] Loading core.hostname grain
    [TRACE   ] Loading core.get_master grain
    [TRACE   ] Loading core.pythonversion grain
    [TRACE   ] Loading core.path grain
    [TRACE   ] Loading core.get_server_id grain
    [TRACE   ] Loading core.ip6 grain
    [TRACE   ] Loading core.ip4 grain
    [TRACE   ] Loading core.saltversion grain
    [TRACE   ] Loading core.saltpath grain
    [TRACE   ] Loading core.pythonexecutable grain
    [TRACE   ] Loading core.fqdn_ip4 grain
    [TRACE   ] Loading core.fqdn_ip6 grain
    [TRACE   ] Loading core.ip6_interfaces grain
    [TRACE   ] Loading core.ip4_interfaces grain
    [TRACE   ] Loading core.append_domain grain
    [TRACE   ] Loading core.os_data grain
    [TRACE   ] 'lspci' could not be found in the following search path: ['/usr/local/sbin', '/sbin', '/bin', '/usr/sbin', '/usr/bin', '/root/bin']
    [DEBUG   ] The `lspci` binary is not available on the system. GPU grains will not be available.
    [TRACE   ] Loading core.zmqversion grain
    [TRACE   ] Loading core.saltversioninfo grain
    [TRACE   ] Loading core.pythonpath grain
    [TRACE   ] Loading core.id_ grain
    [TRACE   ] Loading core.locale_info grain
    [TRACE   ] Loading core.get_machine_id grain
    [TRACE   ] Loading core.ip_interfaces grain
    [TRACE   ] Device sda does not report itself as an SSD
    [TRACE   ] Device dm-0 does not report itself as an SSD
    [TRACE   ] Device dm-1 does not report itself as an SSD
    [INFO    ] The salt minion is starting up
    [INFO    ] Minion is starting as user 'root'
    [DEBUG   ] Minion 'client1.elasticsearch.local.arnoldbechtoldt.com' trying to tune in
    [DEBUG   ] Initializing new SAuth for ('/etc/salt/pki/minion', 'client1.elasticsearch.local.arnoldbechtoldt.com', 'tcp://127.0.0.1:4506')
    [DEBUG   ] Generated random reconnect delay between '1000ms' and '11000ms' (3355)
    [DEBUG   ] Setting zmq_reconnect_ivl to '3355ms'
    [DEBUG   ] Setting zmq_reconnect_ivl_max to '11000ms'
    [DEBUG   ] Initializing new AsyncZeroMQReqChannel for ('/etc/salt/pki/minion', 'client1.elasticsearch.local.arnoldbechtoldt.com', 'tcp://127.0.0.1:4506', 'clear')
    [DEBUG   ] Decrypting the current master AES key
    [DEBUG   ] Loaded minion key: /etc/salt/pki/minion/minion.pem
    [DEBUG   ] Loaded minion key: /etc/salt/pki/minion/minion.pem
    [DEBUG   ] LazyLoaded jinja.render
    [DEBUG   ] LazyLoaded yaml.render
    [INFO    ] The salt minion is shut down
    [ERROR   ] Minion failed to start:
    Traceback (most recent call last):
      File "/usr/lib/python2.7/site-packages/salt/scripts.py", line 81, in minion_process
        minion.start()
      File "/usr/lib/python2.7/site-packages/salt/cli/daemons.py", line 269, in start
        self.minion.tune_in()
      File "/usr/lib/python2.7/site-packages/salt/minion.py", line 1597, in tune_in
        self.sync_connect_master()
      File "/usr/lib/python2.7/site-packages/salt/minion.py", line 589, in sync_connect_master
        raise six.reraise(*future_exception)
      File "/usr/lib64/python2.7/site-packages/tornado/gen.py", line 812, in run
        yielded = self.gen.send(value)
      File "/usr/lib/python2.7/site-packages/salt/minion.py", line 597, in connect_master
        yield self._post_master_init(master)
      File "/usr/lib64/python2.7/site-packages/tornado/gen.py", line 224, in wrapper
        Runner(result, future, yielded)
      File "/usr/lib64/python2.7/site-packages/tornado/gen.py", line 756, in __init__
        if self.handle_yield(first_yielded):
      File "/usr/lib64/python2.7/site-packages/tornado/gen.py", line 886, in handle_yield
        self.future = convert_yielded(yielded)
      File "/usr/lib64/python2.7/site-packages/tornado/gen.py", line 952, in convert_yielded
        return multi_future(yielded)
      File "/usr/lib64/python2.7/site-packages/tornado/gen.py", line 596, in multi_future
        assert all(is_future(i) for i in children)
    AssertionError
    [WARNING ] ** Restarting minion **
    ...
