# Oozie

This short document will show how to use oozie workflow editor.

* After login to platform at first you need to go to Data catalog tab. 
Choose Submit Transfer, specify file (using link or uploading from your file system),
add title, select category and upload to HDFS by cliking blue Upload button.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/upload_file.jpg)

* Go to Data sets tab, filter for your dataset and click +View button.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/tap_view.jpg)

* You will be redirected to the hue's Metastore Manager. At this step it is important to copy
your organization guid and table name. Those will be used to specify table in oozie workflow.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/org_table_copy.jpg)

* Select `Workflows -> Editors -> Workflows` from the menu bar.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/go_to_workflows.jpg)

* Click on create new workflow button

# TODO - add screen

* Drag HiveServer2 Script to the action filed.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/drag_hive_server.jpg)

* Choose your sql script.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/choose_sql_sript.jpg)

* You can upload your script to HDFS or select it if already exist.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/select_script.jpg)

* Confirm by clicking Add button.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/add_sql_script.jpg)

* You can preview and edit your script by clicking small arrow button selected on the picture below.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/sql_preview.jpg)
![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/sql_code_preview.jpg)

* Then add your parameters and save workflow by clicking on the save button in the right corner.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/save_workflow.jpg)

* To start click start button and subbmit.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/start_workflow.jpg)

* Process will look as shown below. Selected button moves you to logs.

![](https://github.com/pprzekwa/FAQs/blob/DPNG-9509-oozie-usage/images/oozie_man/workflow_in_progres.jpg)





