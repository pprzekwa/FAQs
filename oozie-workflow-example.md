# Using Oozie Workflow Scheduler on TAP

### Data Catalog Ingestion

In order to use [Oozie](http://oozie.apache.org/) on TAP you need to import some external dataset.
To do so, follow the steps from [here](https://github.com/trustedanalytics/platform-wiki-0.7/wiki/Data-Catalog-Ingestion).
If your import succeded, you can easly proceed to [Hue](http://gethue.com/) by selecting it as a `Tool for visualization` and clicking on **View** button as show on the last picture. 

### Running Hive queries

The **View** button will redirect you to the Hue's **Metastore Manager**. At this step it is important to copy
your organization guid and table name. Those will be used to specify tablename parameter in oozie workflow.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/org_table_copy.jpg)

Rest of the preocedure is precisly shown on [offcial Hue's website](http://gethue.com/new-apache-oozie-workflow-coordinator-bundle-editors/).

**NOTE:** You will need to use previously copied organization guid and table name by passing them in form of `<organization_guid>.<table_name>` as tablename parameter. 

### Using Shell Action in Oozie

Oozie enables you to put shell scripts to your workflow as well. [Here](http://gethue.com/use-the-shell-action-in-oozie/) is an instruction how to use it.

### Running Python Scripts in Oozie

Running Python scripts is similar to running bash. You need to create shell action and pass python script as a parameter instead of bash.

**NOTE:** While running your scripts make sure you don't have hidden characters in your shebang.

### Runing Spark action in Oozie

To run Spark action you need to drag it to desired workflow field when creating your Workflow in UI.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/spark-job-creation.png)
<br />
![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/upload-path.png)

Information how to fill Spark Master and Mode can be found [here](http://gethue.com/use-the-spark-action-in-oozie/).
To add your jar file click on the button with two dots placed next to **Jar/py files** filed, select **Workspace** and then **lib** catalog. Upload your jar file inside **lib/** directory. After returning to Workflow view ensure that your **Jar/py files** field has only jar file name (<file>.jar) - it is important because jars are searched by default in **Workspace/lib/** directory and paths like **lib/<your-jar-file>.jar** are not allowed. Give a name to your action, specify main class and add arguments if needed. Last step is to save and run your newly created workflow.

**Note:** To test this solution you can create simple spark job following [this Spark Quick Start tutorial](https://spark.apache.org/docs/1.6.0/quick-start.html#self-contained-applications).













