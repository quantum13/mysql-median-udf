mysql-median-udf
================

A UDF to calculate medians in MySQL.

Build Instructions
------------------

1. Switch to the src directory, and run the command for your OS:

  `OSX: gcc -bundle -o udf_median.so udf_median.cc -I/usr/local/include/mysql -m64 -stdlib=libstdc++ -lstdc++`
  `LINUX: gcc -shared -o udf_median.so udf_median.cc -I/usr/include/mysql -m64 -lstdc++ -fPIC`

  This will generate udf_median.so

2. Open your MySQL client, and run `SHOW VARIABLES;` and look for `plugin_dir`

3. Copy the udf_median.so to that directory.

4. Run this in your MySQL client:

  `CREATE AGGREGATE FUNCTION median RETURNS REAL SONAME 'udf_median.so';`