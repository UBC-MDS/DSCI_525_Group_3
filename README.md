# DSCI_525_Group_3

## Description
This project is aimed at exploring useful tools for working with big data. In the report, we compare the runtimes for loading the big size `*.csv` file (e.g.5GB) with different techniques (e.g. changing data type, specifying columns, and loading in chuncks), and the runtimes for transferring dataframe from python to R with two methods (e.g. via parquet file and arrow exchange). Morevover, the time comparison is performed across different operation systems.

## Outline
The project includes multiple steps.
1. Downloading the data from figshare into local computer
2. Combining aggregated csv files into one big csv file
3. Loading the combined csv to memory to perform simple EDA with different approaches:
  - Changing data type from float64 to float 32
  - Loading specified columns instead of the defualt all columns
  - Loading in chunks
  > General observations: with the 3 approaches, we observe that the memory usage is significantly reduced and the processing time becomes faster when performing simple EDA (e.g. value_counts).

4. Comparing two approaches when transferring the dataframe from python to R:
  - Parquet file
  > Overall, parquet format can significantly reduce the size of the files, and in return, it reduces the I/O and network traffic. Reduction in the I/O and network traffic is good when processing big data. The advantages of using parquet file and its processing time for transferring dataframe are provided in our final report.

  - Arrow exchange
  > Arrow can work with parquet file as well as csv files. Arrow can greatly improve performances when moving data between Python and R. We do not need to write the dataframe to parquet file first in python, and then read the parquet file to R, or vice verse. Arrow also has the following advantage:

    - Whenever possible, Arrow will read and process data in chunks and in parallel automatically.
    - Columnar Memory Format
    - Language-independent
    - Zero-copy Reads
    - Minimum Serialization

5. Finally, we also compare the runtime across different operation systems within team members. The results are tabulated in the table below.

<div align="center"> Table 1. Time comparison between machines for combining data </div>

<div align="center">
  
Team Member | Operating System | RAM | Processor | Is SSD | Time taken
-- | -- | -- | -- | -- | --
Member 1 | MacOS Monterey  | 16Gb  | i5  | Yes | 5m 55s
Member 2 |macOS Big Sur 11.5.2|   8GB   |  Apple M1 |    yes    |    6min 8s    |
Member 3 | Win 10   |8Gb   | Ryzen 7  | Yes | 11m 17s
Member 4 |   |   |   |   | 
  
</div>


<div align="center"> Table 2. Time comparison for EDA between machines after reducing memory usage </div>

Team Member | Operating System | RAM | Processor | Is SSD | EDA | Method of optimization |Time before optimization| Time after optimization
-- | -- | -- | -- | -- | -- | -- | -- | -- 
Member 1 | MacOS Monterey  | 16Gb  | i5  | Yes | Describe | Type Conversion|9.12s | 9.33s
Member 1 | MacOS Monterey  | 16Gb  | i5  | Yes | Value_counts | Reading specific columns| 1min 9s | 46.6s
Member 1 | MacOS Monterey  | 16Gb  | i5  | Yes | Value_counts | Chunk processing| 1min 12s | 1min 2s
Member 2 |macOS Big Sur 11.5.2|   8GB |  Apple M1 |    Yes | Describe | Type Conversion|  8.18s | 7.94s
Member 2 |macOS Big Sur 11.5.2|   8GB |  Apple M1 |    Yes | Value_counts | Reading specific columns|  1min 5s | 51.4s
Member 2 |macOS Big Sur 11.5.2|   8GB |  Apple M1 |    Yes | Value_counts | Chunk processing|  1min 5s | 49.1s
Member 3 | Win 10 | 8Gb  | Ryzen 7  | Yes | Describe | Type Conversion|38.1s | 12.5s
Member 3 | Win 10  | 8Gb  | Ryzen 7  | Yes | Value_counts | Reading specific columns| 2min 42s | 1min 36s
Member 3 | Win 10  | 8Gb  | Ryzen 7  | Yes | Value_counts | Chunk processing| 2min 52s | 1min 32s
Member 4 |   |   |   |   |  |  |  |  |
