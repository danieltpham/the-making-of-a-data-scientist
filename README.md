# The making of a Data Scientist

## Chapter XX. Things they did not teach at University

1. Parallel Processing with Apache Spark
* This is technically in the domain of Big Data Analytics, not purely ML
* Hadoop is the framework; Spark is the engine
* PySpark is the Python API for Spark
* **Installation (as of May 2020) tutorial**: https://medium.com/@naomi.fridman/install-pyspark-to-run-on-jupyter-notebook-on-windows-4ec2009de21f 
  * *3 things in the guide that beginners may want to Google cause it's a bit vague:*
   * Change system PATH & ENV 
   * Don't download the most up-to-date version of Java, download the **Java 8** from the link in the article - note that you need to sign up an Oracle account for this 
   * Download & install **7.ZIP** in order to extract the .gz file from Apache Spark
  * *Note: You can simply just install the Anaconda package PySpark, but we would like to learn how to set up a standalone Spark cluster so that we can do a lot more with deployment later (i.e. not dependent on Anaconda). Therefore this method, albeit more complicated steps, is preferred.*
 * **[Parquet format](https://image.slidesharecdn.com/parquet-format-140902013813-phpapp02/95/inside-parquet-format-4-638.jpg?cb=1409622133)**: Parquet stores binary data in a column-oriented way. Most data stored on S3 are in parquet format. Pandas DF can be converted into parquet format with the method `.to_parquet()`
  

