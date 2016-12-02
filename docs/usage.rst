========
Usage
========

To use hpcc_i_spark in a project::

    import hpcc_i_spark

Functionality
--------

* find_record_structure 
Usage: find_record_structure(logical_filename, hpcc_cluster_ip)
Find the record structure of a logical filename
Parameters:
- logical_filename: Logical filename of the file to be sampled. For e.g. vivek::data::c_ecolids.csv
- hpcc_cluster_ip: IP address of THOR

Example:

>>> logical_filename='vivek::data::c_ecolids.csv'
>>> thor_ip="152.46.17.96"
>>> record_string = hpcc_i_spark.find_record_structure(logical_filename, thor_ip)
>>> record_string
'{STRING field1;STRING field2;STRING field3;STRING field4;
STRING field5;STRING field6;STRING field7;STRING field8;
STRING field9;}'


* get_content
Usage: get_content(logical_filename, thor_ip, no_sample)
Get the sampled content of a particular filename at a particular thor cluster. no_sample indicates how many data points (rows) are sampled from each partition of thor clusters. 

Usecase: Assume there is a thor cluster 10.0.2.12 has a logical filename called johndoe.records.csv. 
If the thor cluster has 40 nodes, then  get_content(logical_filename='johndoe.records.csv', thor_ip="10.0.2.12", no_sample=2)
will return 80 records (2 * 40).

Parameters:
- logical_filename: Logical filename of the file to be sampled. For e.g. vivek::data::c_ecolids.csv
- thor_ip: IP address of THOR
- no_sample: Number of samples/cluster. Refer to the usecase for more information

Example:

>>> import hpcc_i_spark
>>> logical_filename = 'vivek::data::c_ecolids.csv'
>>> thor_ip = "152.46.17.96"
>>> no_sample = 2
>>> content = hpcc_i_spark.get_content(logical_filename, thor_ip, no_sample)
>>> content
[[u'1', u'0.49', u'0.29', u'0.48', u'0.5', u'0.56', u'0.24', u'0.35', u'0'],
 [u'10', u'0.42', u'0.4', u'0.48', u'0.5', u'0.56', u'0.18', u'0.3', u'0'], 
 [u'169', u'0.63', u'0.5', u'0.48', u'0.5', u'0.59', u'0.85', u'0.86', u'1',
 [u'170', u'0.49', u'0.42', u'0.48', u'0.5', u'0.53', u'0.79', u'0.81', u'1']]


