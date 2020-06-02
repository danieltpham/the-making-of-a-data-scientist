# The making of a Data Scientist

## Chapter XX. Things they did not teach at University

### (To-write) **Environment, Framework & Engine**
### (To-write) **AWS / AWS Sagemaker**
### (To-learn) **Docker (deploying)**

### 1. **Parallel Processing with Apache Spark `PySpark`**
* This is technically in the domain of Big Data Analytics, not ML
* Hadoop is the framework; Spark is the engine
* PySpark is the Python API for Spark
* **[Installation (as of May 2020) tutorial](https://medium.com/@naomi.fridman/install-pyspark-to-run-on-jupyter-notebook-on-windows-4ec2009de21f)** 
  * *3 things in the guide that beginners may want to Google cause it's a bit vague:*
   * Change system PATH & ENV 
   * Don't download the most up-to-date version of Java, download the **Java 8** from the link in the article - note that you need to sign up an Oracle account for this 
   * Download & install **7.ZIP** in order to extract the .gz file from Apache Spark
  * *Note: You can simply just install the Anaconda package PySpark, but we would like to learn how to set up a standalone Spark cluster so that we can do a lot more with deployment later (i.e. not dependent on Anaconda). Therefore this method, albeit more complicated steps, is preferred.*
 * **[Parquet format](https://image.slidesharecdn.com/parquet-format-140902013813-phpapp02/95/inside-parquet-format-4-638.jpg?cb=1409622133)**: Parquet stores binary data in a column-oriented way. Most data stored on S3 are in parquet format. Pandas DF can be converted into parquet format with the method `.to_parquet()`
 * **[Steps in using Keras with PySpark in Jupyter Notebook:](https://github.com/danieltpham/the-making-of-a-data-scientist/blob/master/helloSpark.ipynb)**
   * Open a PySpark session
   * Transform train/test set into RDD / parquet format with `.to_parquet()` or `.parallelize(numSlices)`
   * Instantiate & compile a Keras model
   * Use **Elephas** or **SparkDL** to convert Keras model to a Pipeline usable by Spark
   * Fit & Train the model (*Note: For classical ML, use `spark.ml` models instead of `scikitlearn` models. For DL, you have to train a model in `keras` first & load it onto `pyspark`*)
   * Get prediction with SparkSQL commands `.select(label)`
   * Close the PySpark session
  
### 2. GAN [(Project `Hello GAN`)](https://github.com/danieltpham/the-making-of-a-data-scientist/blob/master/helloGAN/helloGAN.ipynb)
* GAN is a combined model of 2 networks: generator & discriminator. GAN helps to generate images.
* **[Steps in creating a GAN model in Keras:]**(https://towardsdatascience.com/writing-your-first-generative-adversarial-network-with-keras-2d16fd8d4889)
  * Create a class with `__init__` function, and two attributes: `gan.discriminator()` and `gan.generator()`, created by build functions
  * Combine the two attributes as one with `Model(z, validity)`
  * Define the two build functions, which are 2 `Sequential()` models
  * Define the train function as follows:
    * Generate image from random noise data
    * Calculate loss with the discriminator
    * Update and save the weights for the generator & recombine
    * After `n` epoches, output a test image & save
  * Instantiate a `GAN()` object, and call the `train` function
  
