===============================
hpcc_i_spark
===============================

.. image:: https://img.shields.io/travis/vivekaxl/hpcc_i_spark.svg
        :target: https://travis-ci.org/vivekaxl/hpcc_i_spark

.. image:: https://img.shields.io/pypi/v/hpcc_i_spark.svg
        :target: https://pypi.python.org/pypi/hpcc_i_spark


This package can be used to sample a dataset (given the logical filename) from a HPCC cluster. 
The dataset is returned as a list of list and this can then be used to build models using scikit learn. 
This can also be used to create RDD in the following way:
::

	# Getting the content of the logical file from a ip. We only sample 2 points from each partition
	content = get_content(logical_filename='vivek::data::c_ecolids.csv', thor_ip="152.46.17.96", no_sample=2)
    
	# Convert the data from string to appropriate data type- float in this case
	content = map(lambda c: map(float, c), content)
    
	# Convert to RDD
	rows_rdd = sc.parallelize((content))


* Free software: MIT license
* Documentation: https://hpcc_i_spark.readthedocs.org.
