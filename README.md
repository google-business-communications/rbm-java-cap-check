# RCS BUSINESS MESSAGING: Bulk Capability Check Tool

This sample demonstrates how to use the [RCS Business Messaging Java client library](https://github.com/google-business-communications/java-rcsbusinessmessaging) for performing operations
with the [RCS Business Messaging API](https://developers.google.com/business-communications/rcs-business-messaging/reference/rest)
to execute a bulk capability check against an input list of  phone numbers.

The output of the script will show the potential reachability of the provided users based on random sampling. If your
RBM agent is launched, the script will also output all reachable phone numbers for the carriers in which your agent is
launched for.

This application assumes that you're signed up with
[RCS Business Messaging](https://developers.google.com/business-communications/rcs-business-messaging/guides/get-started/register-partner).

## Documentation

The documentation for the RCS Business Messaging API can be found [here](https://developers.google.com/business-communications/rcs-business-messaging/reference/rest).

## Prerequisite

You must have the following software installed on your machine:

* [Apache Maven](http://maven.apache.org) 3.3.9 or greater
* [Java 8](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

## Before you begin

1.  [Register with RCS Business Messaging](https://developers.google.com/business-communications/rcs-business-messaging/guides/get-started/register-partner).
1. Open the Business Communications Developer Console (https://business-communications.cloud.google.com/console/) with your registered
    Google account and create a new RBM agent.
1. When the agent is available, click the agent's card.
1. In the left navigation, click **Service account**.
1. Click **Create key**, then click **Create**. Your browser downloads a service account key for
    your agent. You need this key to make RBM API calls as your agent.
1. Rename the service account key "rbm-agent-service-account-credentials.json" and move it
    into the "rbm-java-cap-check/src/main/resources" directory.

## Execute the sample

1. In a terminal, navigate to this sample's root directory.

1. Run the following commands:

mvn compile && mvn exec:java -Dexec.args="INPUT_FILE OUTPUT_FILE NUM_OF_THREADS START_INDEX END_INDEX"

The NUM_OF_THREADS, START_INDEX and END_INDEX parameters are optional. By default, the NUM_OF_THREADS is set to 10,
but you can use this option to increase the value. The START_INDEX and END_INDEX parameters select a subset of
numbers from the INPUT_FILE.

## Sample configuration

Prior to running this script with a large amount of threads, you should adjust the default Java
memory allocation by setting the Maven run options with the following command:

export MAVEN_OPTS="-Xms1024m -Xmx3000m"

In our tests, this script using only a single thread can check the capability of 1,000,000 devices in about 2 minutes
running on a MacBook Pro with 2.8 GHz Quad-Core Intel Core i7 CPU and 16 GB of RAM. With the default of 10 threads,
this program can check 1,000,000 users in about 15 seconds.

## Learn more

To learn more about setting up RCS Business Messaging see the
[documentation](https://developers.google.com/business-communications/rcs-business-messaging/guides/get-started/how-it-works).
