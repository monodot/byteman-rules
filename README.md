# byteman-rules

Rules for [Byteman][byteman] for applications to make it easier to debug/log stuff.

Get Byteman, either [direct from the homepage][byteman] or use **dnf** to install Byteman into `/usr/share/byteman`:

    $ sudo dnf install byteman
    $ export BYTEMAN_HOME=/usr/share/byteman

Clone this repository to download the rules:

    $ git clone https://github.com/monodot/byteman-rules
    $ export BYTEMAN_RULES=$(pwd)/byteman-rules

To attach Byteman rule(s) to your app:

    $ cd your-java-app

    $ mvn clean install

    $ java -javaagent:$BYTEMAN_HOME/lib/byteman.jar=script:$BYTEMAN_RULES/a-rule.btm \
        -jar target/your-java-app-1.0-SNAPSHOT.jar

To attach multiple rules to an app:

    $ java -javaagent:/usr/share/byteman/lib/byteman.jar=script:some-rule.btm,script:another-rule.btm \
        -jar target/your-java-app-1.0-SNAPSHOT.jar

## The rules

| Filename | What it contains |
| --- | --- |
| jta_transaction.btm | Rules to trace a [Transaction][transaction] |
| jta_xaresource.btm | Rules to trace [XAResource][xaresource] for XA transactions |

[byteman]: https://byteman.jboss.org/
[xaresource]: https://javaee.github.io/javaee-spec/javadocs/javax/transaction/xa/XAResource.html
[transaction]: https://javaee.github.io/javaee-spec/javadocs/javax/transaction/Transaction.html
