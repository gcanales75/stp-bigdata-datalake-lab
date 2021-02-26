+++
title = "Glue transfomation"
date = 2021-02-17T17:04:42-06:00
weight = 5
chapter = false
pre = "<b>4. </b>"
+++

## Lab 4: Transforming Data with AWS Glue

The IT team at UnicornNation is looking for a way to reduce their AWS spend for this project. After reviewing the file formats they are using, they have decided that for the Merchandise Sales data, they are going to change the file format from CSV to Parquet. 

Parquet is a columnar, compressed format and will help them reduce the amount of data that is scanned when using Amazon Athena.

In this lab, you are going to create a Glue Job to convert the existing CSV data files to Parquet.