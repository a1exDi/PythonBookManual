# pip

**PIP**

Commands:

install Install packages.

download Download packages.

uninstall Uninstall packages.

freeze Output installed packages in requirements format.

list List installed packages.

show Show information about installed packages.

check Verify installed packages have compatible dependencies.

search Search PyPI for packages.

wheel Build wheels from your requirements.

hash Compute hashes of package archives.

completion A helper command used for command completion.

help Show help for commands.

General Options:

-h, --help Show help.

--isolated Run pip in an isolated mode, ignoring environment variables and user

```text
                          configuration.
```

-v, --verbose Give more output. Option is additive, and can be used up to 3 times.

-V, --version Show version and exit.

-q, --quiet Give less output. Option is additive, and can be used up to 3 times

```text
                          \(corresponding to WARNING, ERROR, and CRITICAL logging levels\).
```

--log &lt;path&gt; Path to a verbose appending log.

--proxy &lt;proxy&gt; Specify a proxy in the form \[user:passwd@\]proxy.server:port.

--retries &lt;retries&gt; Maximum number of retries each connection should attempt \(default 5 times\).

--timeout &lt;sec&gt; Set the socket timeout \(default 15 seconds\).

--exists-action &lt;action&gt; Default action when a path already exists: \(s\)witch, \(i\)gnore, \(w\)ipe,

```text
                          \(b\)ackup, \(a\)bort.
```

--trusted-host &lt;hostname&gt; Mark this host as trusted, even though it does not have valid or any HTTPS.

--cert &lt;path&gt; Path to alternate CA bundle.

--client-cert &lt;path&gt; Path to SSL client certificate, a single file containing the private key and

```text
                          the certificate in PEM format.
```

--cache-dir &lt;dir&gt; Store the cache data in &lt;dir&gt;.

--no-cache-dir Disable the cache.

--disable-pip-version-check

```text
                          Don't periodically check PyPI to determine whether a new version of pip is

                          available for download. Implied with --no-index.
```

