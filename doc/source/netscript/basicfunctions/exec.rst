exec() Netscript Function
=========================

.. js:function:: exec(script, hostname[, numThreads=1[, args...]])

    :RAM cost: 1.3 GB

    :param string script: Filename of script to execute.
    :param string hostname: Hostname of the target server on which to execute the script.
    :param number numThreads: Optional thread count for new script. Set to 1 by
        default. Has to be an integer.
    :param args...: Additional arguments to pass into the new script that is
        being run. Note that if any arguments are being
        passed into the new script, then the third argument ``numThreads`` must
        be filled in with a value.
    :returns: Newly created process id (PID) on success, 0 on failure.

    Run a script as a separate process on a specified server. This is similar to
    the :doc:`run<run>` function except that it can be used to run a script on any
    server, instead of just the current server.

    .. warning:: Running this function with a ``numThreads`` argument of 0 or
                 less will cause a runtime error.

    The simplest way to use the :doc:`exec<exec>` command is to call it with
    just the script name and the target server. The following example will try
    to run ``generic-hack.js`` on the ``foodnstuff`` server::

        ns.exec("generic-hack.js", "foodnstuff");

    The following example will try to run the script ``generic-hack.js`` on
    the ``joesguns`` server with 10 threads::

        ns.exec("generic-hack.js", "joesguns", 10);

    This last example will try to run the script ``foo.js`` on the
    ``foodnstuff`` server with 5 threads. It will also pass the number 1 and the
    string "test" in as arguments to the script::

        ns.exec("foo.js", "foodnstuff", 5, 1, "test");
