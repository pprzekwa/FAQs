# Creating Oozie workflow
Creating simple workflow with Hive query as example of using Oozie with Hue.

* Login to platform and find **Data catalog** -> **Submit Transfer** tab. 
 Fill the form and confirm by clicking on the **Upload** button.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/upload_file.jpg)

* After successful upload switch to **Data sets** tab. Filter for your dataset and open it in Hue by clicking **+View button**.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/tap_view.jpg)

* You will be redirected to the Hue's **Metastore Manager**. At this step it is important to copy
your organization guid and table name. Those will be used to specify tablename parameter in oozie workflow.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/org_table_copy.jpg)

* Select **Workflows** -> **Editors** -> **Workflows** from the menu bar.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/go_to_workflows.jpg)

* Create new workflow.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/create_workflow.jpg)

* Drag **HiveServer2 Script** to the action filed.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/drag_hive_server.jpg)

* Choose file with sql query.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/choose_sql_sript.jpg)

* Upload your script to HDFS or select it if already exist.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/select_script.jpg)

* Confirm by clicking **Add** button.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/add_sql_script.jpg)

* (Optional) It is possible to preview and edit script by clicking on small arrow distinguished on the picture below.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/sql_preview.jpg)
![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/sql_code_preview.jpg)

* Add your parameters and save workflow by clicking on the save button in the right corner. <br />
**NOTE:** here you need to use previously copied organization guid and table name by passing them in `<organization_guid>.<table_name>` form as tablename parameter. 

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/save_workflow.jpg)

* To start use start button and subbmit.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/start_workflow.jpg)

* Process will look as shown below. (Button in red rectangle moves you to **logs**)

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/workflow_in_progress.jpg)

* See results by clicking on button in red rectangle.
 
![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/done_100.jpg)

* Results of our query are shown below.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/final_results.jpg)




