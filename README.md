Fesen Runner
============

This project runs Fesen cluster on one JVM instance for your development/testing easily.
You can use Fesen Runner as Embedded Fesen in your application.

## Version

[Versions in Maven Repository](https://repo1.maven.org/maven2/org/codelibs/fesen-runner/)

## Run on Your Application

Put fesen-runner if using Maven:

    <dependency>
        <groupId>org.codelibs.fesen</groupId>
        <artifactId>fesen-runner</artifactId>
        <version>x.x.x.0</version>
    </dependency>

### Start Runner

    import static org.codelibs.fesen.runner.FesenRunner.newConfigs;
    ...
    // create runner instance
    FesenRunner runner = new FesenRunner();
    // create ES nodes
    runner.onBuild(new FesenRunner.Builder() {
        @Override
        public void build(final int number, final Builder settingsBuilder) {
            // put fesen settings
            // settingsBuilder.put("index.number_of_replicas", 0);
        }
    }).build(newConfigs());

build(Configs) method configures/starts Clsuter Runner.

### Stop Runner

    // close runner
    runner.close();

### Clean up 

    // delete all files(config and index)
    runner.clean();

## Run on JUnit

Put fesen-runner as test scope:

    <dependency>
        <groupId>org.codelibs.fesen</groupId>
        <artifactId>fesen-runner</artifactId>
        <version>x.x.x.0</version>
        <scope>test</scope>
    </dependency>

and see [FesenRunnerTest](https://github.com/codelibs/fesen-runner/blob/master/src/test/java/org/codelibs/fesen/runner/FesenRunnerTest.java "FesenRunnerTest").

## Run as Standalone

### Install Maven

Download and install Maven 3 from http://maven.apache.org/.

### Clone This Project

    git clone https://github.com/codelibs/fesen-runner.git

### Build This Project

    mvn compile

## Run/Stop Fesen Cluster

### Run Cluster

Run:

    mvn exec:java 

The default cluster has 3 nodes and the root directory for Fesen is es\_home.
Nodes use 9201-9203 port for HTTP and 9301-9303 port for Transport.
If you want to change the number of node, Run:

    mvn exec:java -Dexec.args="-basePath es_home -numOfNode 4"

### Stop Cluster

Type Ctrl-c or kill the process.
