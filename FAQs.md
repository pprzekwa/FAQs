> [Wiki Home](Home) ▸ **FAQs**


## Applications and Deployment FAQs

**Q: How do I deploy an example Java application?**<br />
    ```
    git clone https://github.com/cloudfoundry-samples/spring-music.git
    cd spring-music
    ./gradlew assemble
    cf push
    ```

If you are developing your own application with Maven:

    vim manifest.yml # see https://github.com/cloudfoundry-samples/spring-music/blob/master/manifest.yml for reference
    mvn clean package
    cf push -n [hostname] # your application will be visible under [hostname].domain.com
   

**Q: My application didn't run on CF. What should I do?**

* Check if your jar is working:<br>
    `java -jar target/[jar-name].jar`

* Check cf logs<br>
    `cf logs [app-name] --recent`

* If you get _ERR Instance (index 0) failed to start accepting connections_...
    - try to change the memory in manifest to 512 MB or 1 GB; or 
    - verify that you didn't use a specific port.

**Q: How do I provision a sample (PostgreSQL) service?**<br />

    cf create-service postgresql93 free spring-music-pg
    cf bind-service spring-music spring-music-pg
    cf restart spring-music

**Q: How can I get a shell session for my application?** <br />

You can get a new container in Cloud Foundry containing your application code with the _cf-ssh_ tool. See https://blog.starkandwayne.com/2014/07/14/running-one-time-tasks-in-cloud-foundry/

**Q: How do I run Warden on the runner machine to troubleshoot a container?**

On the jump box:

    `bosh ssh runner_z1/0`
    `export PATH=/var/vcap/packages/ruby/bin:$PATH`
    `cd /var/vcap/data/packages/warden/<TAB>/warden`
    `./bin/warden --socket /var/vcap/data/warden/warden.sock`

From that point, you can do the things as specified in [the Cloud Foundry troubleshooting docs] (http://docs.cloudfoundry.org/running/troubleshooting/troubleshooting-warden-services.html).

**Q: Where do I get cf-ssh?** <br />

You can read a [blog post about it](https://blog.starkandwayne.com/2014/07/14/running-one-time-tasks-in-cloud-foundry/) or you can just do the following:

```
cd ~/bin  
wget https://raw.githubusercontent.com/danhigham/tmate-bootstrap/master/scripts/cf-ssh -O cf-ssh  
chmod +x cf-ssh 
```

**Q: How do I view the current memory and disk usage of Cloud Foundry?**<br />

Log on to the jumpbox and run the _dea_ads_ command.

**Q: I created a service on Marketplace. How can I access it from my application?**<br />

Firstly, you need to bind your application to the service. It can be done by executing the following command:

	cf bind-service your-app your-service

Then you need to restart or in some cases re-push you application. As a result credentials for the service instance will be delivered to the application runtime in environment variable named VCAP_SERVICES. For more explicit information read [the Cloud Foundry docs.] (http://docs.cloudfoundry.org/devguide/services/application-binding.html#bind)

Here you can find some of ours implementatuion examples:

* [Java] (https://github.com/trustedanalytics/user-management/blob/8fc3dd4bec931d446ab05a04dbd84b4a4049ed26/src/main/java/org/trustedanalytics/user/invite/config/StorageConfig.java#L90-L112#bind) <br>
* [Golang] (https://github.com/trustedanalytics/application-broker/blob/3593eca396848e9fe67709df3fe8508d6d69fcd0/dao/mongo.go#L17-L51#bind) <br>
* [Python] (https://github.com/trustedanalytics/data-catalog/blob/master/data_catalog/configuration.py#L30-L108#bind) <br>

In case of Spring projects we also encourage you to read [Cloud Foundry documentation] (https://docs.cloudfoundry.org/buildpacks/java/spring-service-bindings.html#bind) on this topic. <br>

**Q: How do I view all the current logs within Cloud Foundry?**<br />

Log on to the jumpbox and run the _nats_sub_ command.

**Q: What languages and frameworks are inherently supported with Trusted Analytics Platform?**<br />
Java, python, nodejs, scala, go, ruby, PHP  

| Language | Runtime | Framework |
| -------- | ------- | --------- |
| Java | Java 6, Java 7, Java 8 | Spring Framework 3.x, 4.x   |
| Ruby | Ruby 1.8, Ruby 1.9, Ruby 2.0 | Rails, Sinatra   |
| Node.js | V8 JavaScript Engine (from Google Chrome) | Node.js |
| Scala | Scala 2.x | Play 2.x, Lift   |
| Python |  | Python   |
| PHP |  | PHP |

              
**Q: Does Trusted Analytics Platform support all common buildpacks traditionally supported with Cloud Foundry?**<br />
Yes:

| buildpack | download |
| --------- | -------- |
| java_buildpack       | java-buildpack-v3.0.zip    |
| ruby_buildpack       | ruby_buildpack-cached-v1.3.0.zip    |
| nodejs_buildpack     | nodejs_buildpack-cached-v1.2.1.zip    |
| go_buildpack         | go_buildpack-cached-v1.2.0.zip    |
| python_buildpack     | python_buildpack-cached-v1.2.0.zip    |
| php_buildpack        | php_buildpack-offline-v3.1.0.zip    |
| staticfile_buildpack | staticfile_buildpack-cached-v1.0.0.zip    |

 
**Q: What is the dependency of Trusted Analytics Platform on CDH?**<br />
The platform depends on CDH to provide big data capabilities and to be able to use the Analytics Toolkit (ATK). At this moment, TAP doesn't support any other distribution of Apache Hadoop.

**Q: What tools can be used with the Analytics Toolkit?**<br />
The Analytics Toolkit can be accessed using Python. The Analytics Toolkit also requires CDH with Spark running on it.

**Q: What data is supported in the Console > Data Catalog > Submit Transfer?**<br />
Any data set that  is publicly available via http protocol, can be downloaded to TAP.
Additional ways to obtain data include
- Client (Data producers) —> Websocket —> Kafka —> HDFS
- Client (Data producers) —> MQTT broker —> HDFS

**Q: Where can I find a list of all supported CF commands?**<br />
All Cloud Foundry  cli commands documentation can be found at www.cloudfoundry.org
Also `cf —help` will list all available commands.

## Admin and User Management FAQs

**Q: In Console > User management, what is the difference between “space” and “organization”?**<br />
Hierarchy is that an _organization_ contains a _space_.
You can think of a _space_ much like a department within an organization.
There is no fixed meaning to _space_; you may use this subdivision as you wish.
For instance, “dev”, “test”, or “prod” are good space names.
A user must be a "space developer" in order to deploy applications.

**Q: How do I add new services to Console > Marketplace?**<br />
There are Cloud Foundry commands to add services to Marketplace.
Please refer to Cloud Foundry documentation for development of new services (how to code a new service).

**Q: How much time should I give an application to re-stage?**<br />
It depends on the application start-up procedure. If the application start-up procedure is long, it will take time.

**Q: How do I configure an application to automatically re-stage or deploy another instance of itself?**<br />
- Write scripts on Unix to automatically re-stage using cf command line.
- There is automatic pay increase or decrease instance. Cf command line can be used to deploy another instance.
- There are ample opportunities to write application-specific scaling scripts.

## Open Source FAQs

**Q. What is the governance model of this project?**<br />

It is our intention in the Trusted Analytics Platform engineering community to follow an open and democratic model found in many of the Apache Foundation's open source projects. The model is based on earned leadership. 

As developers demonstrate their abilities by contributing new code and documentation to the Trusted Analytics project, and their contributions are acknowledged by the existing members by pulling their requests, those individual contributors will gain greater responsibility in decision-making of our project. See [How the Apache Software Foundation Works](http://www.apache.org/foundation/how-it-works.html)


**Q. What part of the project needs the most contributions?**

Analytical Tooling 

* [The Analytics Toolkit](https://github.com/trustedanalytics/atk)
* [The Analytics Toolkit Buildpack](https://github.com/trustedanalytics/atk-buildpack)

Installer Tools

* [Platform Parent](https://github.com/trustedanalytics/platform-parent)

Others

* [App Launching](https://github.com/trustedanalytics/app-launching-service-broker)
* [Service Catalog](https://github.com/trustedanalytics/service-catalog)
* [Data Acquisition](https://github.com/trustedanalytics/data-acquisition)

**Q. What elements of this project are in use by other projects?**

Many of the ~30 projects comprising the Trusted Analytics Platform depend on each other; some can stand on their own. All of the projects are developed in a way that should minimize the effort to use them independently.
