# Using Oozie Workflow Scheduler on TAP

### Data Catalog Ingestion

In order to use [Oozie](http://oozie.apache.org/) on TAP you need to import some external dataset.
To do so follow the steps from [here](https://github.com/trustedanalytics/platform-wiki-0.7/wiki/Data-Catalog-Ingestion).
If your import succeded, you can easly proceed to [Hue](http://gethue.com/) by selecting it as a `Tool for visualization` and clicking on **View** button as show on the last picture. 

### Running Hive queries

The **View** button will redirect you to the Hue's **Metastore Manager**. At this step it is important to copy
your organization guid and table name. Those will be used to specify tablename parameter in oozie workflow.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/org_table_copy.jpg)

Rest of this preocedure to one shown on offcial Hue's youtube channel.

[![hue](https://img.youtube.com/vi/l7K-2M_StsY/0.jpg)](https://www.youtube.com/watch?v=l7K-2M_StsY)

**NOTE:** You will need to use previously copied organization guid and table name by passing them in `<organization_guid>.<table_name>` form as tablename parameter. 





